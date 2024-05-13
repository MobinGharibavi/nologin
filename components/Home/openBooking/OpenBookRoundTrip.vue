<template>
  <div class="flex relative items-center gap-2 flex-wrap">
    <div
      @click="firstOrigin = !firstOrigin"
      v-click-outside="clickOutFirstOrigin"
      class="rounded-[16px] relative border border-[#DCDFE4] px-6 py-[10px] flex-grow cursor-pointer"
    >
      <p class="text-sm text-[#938F96]">
        {{ $t("Booking.Boxs.origin.title") }}
      </p>
      <!-- <p class="font-bold">{{ $t("Booking.Boxs.origin.body") }}</p> -->
      <p class="font-bold">
        {{ forSearchOrigin.Country_Name }}, {{ forSearchOrigin.Name }} ({{
          forSearchOrigin.Code
        }})
      </p>
      <!-- {{ JSON.parse(JSON.stringify(cities)).default }} -->
      <div
        class="absolute bottom-0 left-0 top-16 z-50 h-max w-full bg-white shadow-xl rounded-lg px-4"
      >
        <TransitionExpand :duration="500">
          <div
            v-if="firstOrigin"
            class="flex py-2 border-b h-72 overflow-auto flex-col"
          >
            <!-- <h6 class="font-bold">
                {{ $t("Booking.Boxs.origin.subtitle") }}
              </h6>
              <p class="text-gray-600">{{ $t("Booking.Boxs.origin.body") }}</p> -->
            <main
              v-for="(item, index) in JSON.parse(JSON.stringify(cities))
                .default"
              :key="index"
              @click="forSearchOrigin = item"
            >
              <h6 class="font-bold">
                {{ item.Name }}
              </h6>
              <p class="text-gray-600">
                {{ item.Country_Name }}, {{ item.Name }} ({{ item.Code }})
              </p>
            </main>
          </div>
        </TransitionExpand>
      </div>
    </div>
    <div
      @click="firstDestination = !firstDestination"
      v-click-outside="clickOutFirstDestination"
      class="rounded-[16px] relative border border-[#DCDFE4] px-6 py-[10px] flex-grow cursor-pointer"
    >
      <p class="text-sm text-[#938F96]">
        {{ $t("Booking.Boxs.destination.title") }}
      </p>
      <!-- <p class="font-bold">{{ $t("Booking.Boxs.destination.body") }}</p> -->
      <p class="font-bold">
        {{ forSearchDest.Country_Name }}, {{ forSearchDest.Name }} ({{
          forSearchDest.Code
        }})
      </p>
      <div
        class="absolute bottom-0 left-0 top-16 z-50 h-max w-full bg-white shadow-xl rounded-lg px-4"
      >
        <TransitionExpand :duration="500">
          <div
            v-if="firstDestination"
            class="flex py-2 border-b h-72 overflow-auto flex-col"
          >
            <!-- <h6 class="font-bold">
                {{ $t("Booking.Boxs.destination.subtitle") }}
              </h6>
              <p class="text-gray-600">
                {{ $t("Booking.Boxs.destination.body") }}
              </p> -->
            <main
              v-for="(item, index) in JSON.parse(JSON.stringify(cities))
                .default"
              :key="index"
              @click="forSearchDest = item"
            >
              <h6 class="font-bold">
                {{ item.Name }}
              </h6>
              <p class="text-gray-600">
                {{ item.Country_Name }}, {{ item.Name }} ({{ item.Code }})
              </p>
            </main>
          </div>
        </TransitionExpand>
      </div>
    </div>
    <div
      v-click-outside="clickOutFirstDate"
      class="rounded-[16px] border border-[#DCDFE4] px-6 py-[10px] flex-grow cursor-pointer"
    >
      <div @click="firstDate = !firstDate">
        <p class="text-sm text-[#938F96]">
          {{ $t("Booking.Boxs.departure-date.title") }}
        </p>
        <p class="font-bold">
          {{ new Date(range.start).getDate() }}/
          {{ months[new Date(range.start).getMonth()] }}/{{
            new Date(range.start).getFullYear()
          }}
          ~ {{ new Date(range.end).getDate() }}/{{
            months[new Date(range.end).getMonth()]
          }}/{{ new Date(range.end).getFullYear() }}
        </p>
      </div>
      <div
        class="absolute right-0 left-0 lg:left-auto lg:bottom-0 lg:right-40 lg:top-16 z-50 h-max bg-white shadow-xl rounded-lg px-4"
      >
        <TransitionExpand :duration="500">
          <div v-if="firstDate" class="flex flex-col">
            <div
              class="flex flex-col gap-3 lg:flex-row justify-between border-b py-3 items-center"
            >
              <h6 class="text-xl font-bold">
                {{ $t("Booking.Boxs.departure-date.title") }}
              </h6>
              <div class="flex items-center gap-3">
                <span class="text-blue-500 font-semibold cursor-pointer"
                  >Go today</span
                >
                <div class="flex items-center gap-2">
                  <div class="checkbox-wrapper-34">
                    <input
                      v-model="returnDate"
                      class="tgl tgl-ios"
                      @click="changeToday"
                      id="toggle-34"
                      type="checkbox"
                    />
                    <label class="tgl-btn" for="toggle-34"></label>
                  </div>
                  <p class="text-gray-600">Return date</p>
                </div>
              </div>
            </div>
            <div class="m-2 border-b">
              <VDatePicker
                v-model.range="range"
                :columns="columns"
                :locale="loc"
                :expanded="expanded"
              />
            </div>
            <div
              class="flex flex-col lg:flex-row justify-between mb-2 items-center"
            >
              <div
                class="flex items-center bg-gray-100 gap-5 px-1 py-1 rounded-lg"
              >
                <button
                  :class="{ '!text-blue-500 !p-2 bg-white': loc == 'en' }"
                  @click="loc = 'en'"
                  class="text-gray-700 pl-2 rounded-lg"
                >
                  Gregorian
                </button>
                <button
                  @click="loc = 'fa'"
                  :class="{ '!text-blue-500 bg-white': loc == 'fa' }"
                  class="p-2 text-gray-700 rounded-lg"
                >
                  solar calender
                </button>
              </div>

              <div class="flex items-center gap-2 p-2.5">
                <button
                  @click="firstDate = !firstDate"
                  class="rounded-lg w-full flex items-center justify-center px-5 py-2 text-white bg-blue-500"
                >
                  Confirm
                </button>
                <button
                  @click="cancelAndResetCalender"
                  class="rounded-lg w-full flex items-center justify-center px-5 py-2 text-blue-500 border-2 border-blue-500"
                >
                  Cancel
                </button>
              </div>
            </div>
          </div>
        </TransitionExpand>
      </div>
    </div>
    <button
      @click="handleSearchFlight"
      class="rounded-[16px] w-full lg:w-auto mx-auto flex gap-2 items-center justify-center text-white bg-[#0A77FF] py-5 px-10 cursor-pointer"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
      >
        <path
          d="M11.5 21C16.7467 21 21 16.7467 21 11.5C21 6.25329 16.7467 2 11.5 2C6.25329 2 2 6.25329 2 11.5C2 16.7467 6.25329 21 11.5 21Z"
          stroke="white"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M22 22L20 20"
          stroke="white"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
      <p>{{ $t("Booking.search") }}</p>
    </button>
  </div>
</template>

<script setup>
import { useScreens } from "vue-screen-utils";

const { locale } = useI18n();
const cities = await import("~/assets/json/cities.json");
const props = defineProps(["openModal"]);
const router = useRouter();
const returnDate = ref(false);
const loc = ref("en");
// calender
const months = ref([
  "Jan",
  "Feb",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "Sep",
  "Oct",
  "Nov",
  "Dec",
]);
const { mapCurrent } = useScreens({
  xs: "0px",
  sm: "640px",
  md: "768px",
  lg: "1024px",
});
const columns = mapCurrent({ lg: 2 }, 1);
const expanded = mapCurrent({ lg: false }, true);
const range = ref({
  start: Date.now(),
  end: Date.now(),
});

const changeToday = () => {
  if (!returnDate.value) {
    range.value = {
      start: Date.now(),
      end: Date.now(),
    };
  }
};

const cancelAndResetCalender = () => {
  firstDate.value = false;
  range.value = {
    start: new Date(Date.now()),
    end: new Date(Date.now()),
  };
};

const forSearchDest = ref({
  Name: JSON.parse(JSON.stringify(cities)).default[0].Name,
  Code: JSON.parse(JSON.stringify(cities)).default[0].Code,
  Country_Name: JSON.parse(JSON.stringify(cities)).default[0].Country_Name,
});
const firstDestination = ref(false);
const clickOutFirstDestination = () => {
  if (firstDestination.value) {
    firstDestination.value = false;
  }
};

const forSearchOrigin = ref({
  Name: JSON.parse(JSON.stringify(cities)).default[1].Name,
  Code: JSON.parse(JSON.stringify(cities)).default[1].Code,
  Country_Name: JSON.parse(JSON.stringify(cities)).default[1].Country_Name,
});
const firstOrigin = ref(false);
const clickOutFirstOrigin = () => {
  if (firstOrigin.value) {
    firstOrigin.value = false;
  }
};

const firstDate = ref(false);
const clickOutFirstDate = () => {
  if (firstDate.value) {
    firstDate.value = false;
  }
};

const handleSearchFlight = () => {
  router.push({
    path: `/${locale.value}/Filter`,
    query: {
      origin: forSearchOrigin.value.Code,
      destination: forSearchDest.value.Code,
      departure_date_time: new Date(range.value.start).toISOString(),
      return_date_time: returnDate.value
        ? ""
        : new Date(range.value.end).toISOString(),
    },
  });
};
</script>

<style scoped>
:deep(.vc-bordered) {
  @apply !border-none;
}
</style>
