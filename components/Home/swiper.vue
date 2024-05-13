<template>
  <section class="max-w-[1248px] w-full mx-auto bestpromotional mt-14 px-4">
    <h2 class="text-[32px] font-bold text-[#1D1B20] mb-2" id="hotdeals">
      {{ $t("SwiperMain.title") }}
    </h2>
    <!-- Swiper -->
    <ClientOnly>
      <Carousel
        dir="rtl"
        :breakpoints="breakpoints"
        :wrapAround="true"
        :autoplay="2500"
      >
        <Slide v-for="(item, index) in 2" :key="index">
          <div
            class="rounded-[16px] overflow-hidden hover:shadow-xl transition-all"
          >
            <div class="relative overflow-hidden">
              <img
                src="/img/2-(1).png"
                alt=""
                class="w-full rounded-[16px] h-52 object-contain"
              />
            </div>
            <div class="p-3 pb-4 text-center">
              <a class="text-lg font-bold block cursor-pointer">
                {{ $t("SwiperMain.name") }}
              </a>
              <p class="mt-1 text-[#938F96]">
                {{ $t("SwiperMain.description") }}
              </p>
            </div>
          </div>
        </Slide>
        <Slide v-for="(item, index) in 2" :key="index">
          <div
            class="rounded-[16px] overflow-hidden hover:shadow-xl transition-all"
          >
            <div class="relative overflow-hidden">
              <img
                src="/img/2-(3).png"
                alt="..."
                class="w-full rounded-[16px] h-52 object-contain"
              />
            </div>
            <div class="p-3 pb-4 text-center">
              <a class="text-lg font-bold block cursor-pointer">
                {{ $t("SwiperMain.name") }}
              </a>
              <p class="mt-1 text-[#938F96]">
                {{ $t("SwiperMain.description") }}
              </p>
            </div>
          </div>
        </Slide>
        <Slide v-for="(item, index) in 2" :key="index">
          <div
            class="rounded-[16px] overflow-hidden hover:shadow-xl transition-all"
          >
            <div class="relative overflow-hidden">
              <img
                src="/img/2-(4).png"
                alt=""
                class="w-full rounded-[16px] h-52 object-contain"
              />
            </div>
            <div class="p-3 pb-4 text-center">
              <a class="text-lg font-bold block cursor-pointer">
                {{ $t("SwiperMain.name") }}
              </a>
              <p class="mt-1 text-[#938F96]">
                {{ $t("SwiperMain.description") }}
              </p>
            </div>
          </div>
        </Slide>
        <Slide v-for="(item, index) in 2" :key="index">
          <div
            class="rounded-[16px] overflow-hidden hover:shadow-xl transition-all"
          >
            <div class="relative overflow-hidden">
              <img
                src="/img/2-(2).png"
                alt=""
                class="w-full rounded-[16px] h-52 object-contain"
              />
            </div>
            <div class="p-3 pb-4 text-center">
              <a class="text-lg font-bold block cursor-pointer">
                {{ $t("SwiperMain.name") }}
              </a>
              <p class="mt-1 text-[#938F96]">
                {{ $t("SwiperMain.description") }}
              </p>
            </div>
          </div>
        </Slide>
      </Carousel>
    </ClientOnly>
  </section>
</template>

<script setup>
const breakpoints = ref({
  576: {
    itemsToShow: 2,
  },
  768: {
    itemsToShow: 3,
  },
  1020: {
    itemsToShow: 4,
  },
  1280: {
    itemsToShow: 5,
  },
});
</script>
