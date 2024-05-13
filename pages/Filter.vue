<template>
  <main>
    <!-- loader -->
    <UtilsLoading v-if="isFetching" />
    <!-- booking -->
    <FilterBooking :filtered="filtered" :execute="execute" />

    <!-- date -->
    <FilterDate :execute="execute"/>

    <!-- other -->
    <FilterOther :data="data" v-if="isFinished" />
  </main>
</template>

<script setup>
import { useFetch } from "@vueuse/core";
definePageMeta({
  middleware: 'check',
});

const route = useRoute();
const filtered = reactive({
  adults: 1,
  children: 0,
  infants: 0,
});

const cookies = useCookie("access_token");

const { data, isFetching, isFinished, execute } = useFetch(
  "http://65.108.44.215:4001/v1/flight/search/100",
  {
    async beforeFetch({ url, options, cancel }) {
      if (!cookies.value) cancel();

      options.method = "POST";
      options.body = JSON.stringify({
        ...route.query,
        ...filtered,
      });
      options.headers = {
        ...options.headers,
        Authorization: `Bearer ${cookies.value}`,
        "Content-Type": "application/json", // specify content type
      };

      return {
        options,
      };
    },
  },
  { refetch: true }
).json();
</script>
