<template>
  <section class="border-t mt-5 py-4">
    <div class="py-2 max-w-[1248px] mx-auto">
      <ClientOnly>
        <Carousel
          :loop="true"
          :wrapAround="true"
          :autoplay="2500"
          :breakpoints="breakpoints"
        >
          <Slide v-for="(item, index) in date" :key="index">
            <div class="swiper-slide">
              <label
                class="select flex-col rounded-lg text-center border border-transparent transition-all hover:bg-[#E4F0FF] hover:border-[#0A77FF] hover:text-[#0A77FF] w-[129px] h-14 cursor-pointer text-sm text-[#1D1B20] flex items-center justify-center"
                :class="{
                  '!text-[#0A77FF] !border-[#0A77FF] !bg-[#E4F0FF]':
                    correctISO(`${item.date}/${new Date().getFullYear()}`) ===
                    openTab,
                }"
              >
                <input
                  type="radio"
                  v-model="openTab"
                  :value="
                    correctISO(`${item.date}/${new Date().getFullYear()}`)
                  "
                  @click="
                    changeDate(
                      correctISO(`${item.date}/${new Date().getFullYear()}`)
                    )
                  "
                  :checked="
                    correctISO(`${item.date}/${new Date().getFullYear()}`) ===
                    openTab
                  "
                  class="hidden"
                />
                <span class="text">{{ item.date }}</span>
                <span class="font-semibold">{{ item.day }}</span>
              </label>
            </div>
          </Slide>
        </Carousel>
      </ClientOnly>
    </div>
  </section>
</template>

<script setup>
import { addDay, format } from "@formkit/tempo";
const { execute } = defineProps({
  execute: Function,
});
const breakpoints = ref({
  400: {
    itemsToShow: 3,
  },
  576: {
    itemsToShow: 5,
  },
  768: {
    itemsToShow: 7,
  },
  992: {
    itemsToShow: 8,
  },
  1200: {
    itemsToShow: 9,
  },
});
const router = useRouter();
const route = useRoute();
const openTab = ref(route.query.departure_date_time);

const { locale } = useI18n();
const date = ref([]);

for (let i = 0; i < 20; i++) {
  const tt = format(addDay(new Date().toISOString(), i), "dddd", locale.value);
  const dd = format(addDay(new Date().toISOString(), i), "MM/DD", locale.value);
  date.value.push({
    day: tt,
    date: dd,
  });
}

const correctISO = (time) => {
  const [month, day, year] = time.split("/").map(Number);
  const date = new Date(year, month - 1, day);
  date.setDate(date.getDate() + 1);
  return date.toISOString();
};

const changeDate = (date) => {
  openTab.value = date;
  router.push({
    path: `/${locale.value}/Filter`,
    query: {
      origin: route.query.origin,
      destination: route.query.destination,
      departure_date_time: date,
      return_date_time: route.query.return_date_time,
    },
  });
  execute();
};
</script>
