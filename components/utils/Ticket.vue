<template>
  <!-- Modal start -->
  <UtilsModal @close="toogleModal" :modalActive="modalActive">
    <div class="flex flex-col">
      <template v-for="(item, index) in 2" :key="index">
        <div
          class="flex justify-between border-b px-5 py-3 bg-white items-center"
        >
          <div class="flex flex-col">
            <p class="font-semibold text-lg">Tehran(IMK) to Torento</p>
            <div class="flex text-gray-500 items-center gap-5">
              <span>25h 20m</span>
              <span>Wed May 10</span>
            </div>
          </div>
          <div class="text-blue-600 text-xl">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="1em"
              height="1em"
              viewBox="0 0 24 24"
            >
              <g fill="none" fill-rule="evenodd">
                <path
                  d="M24 0v24H0V0zM12.593 23.258l-.011.002l-.071.035l-.02.004l-.014-.004l-.071-.035c-.01-.004-.019-.001-.024.005l-.004.01l-.017.428l.005.02l.01.013l.104.074l.015.004l.012-.004l.104-.074l.012-.016l.004-.017l-.017-.427c-.002-.01-.009-.017-.017-.018m.265-.113l-.013.002l-.185.093l-.01.01l-.003.011l.018.43l.005.012l.008.007l.201.093c.012.004.023 0 .029-.008l.004-.014l-.034-.614c-.003-.012-.01-.02-.02-.022m-.715.002a.023.023 0 0 0-.027.006l-.006.014l-.034.614c0 .012.007.02.017.024l.015-.002l.201-.093l.01-.008l.004-.011l.017-.43l-.003-.012l-.01-.01z"
                />
                <path
                  fill="currentColor"
                  d="M12.707 15.707a1 1 0 0 1-1.414 0L5.636 10.05A1 1 0 1 1 7.05 8.636l4.95 4.95l4.95-4.95a1 1 0 0 1 1.414 1.414z"
                />
              </g>
            </svg>
          </div>
        </div>
      </template>

      <h4 class="m-4">Options</h4>
      <div
        v-for="(item, index) in 4"
        :key="index"
        class="hidden lg:flex border-b justify-between bg-white px-5 py-3 items-center"
      >
        <h6 class="text-purple-500 text-lg font-semibold">Airline Logo</h6>

        <div class="flex gap-5 items-center">
          <span class="flex gap-2 items-center"
            ><p class="text-gray-400 text-sm">USD</p>
            <span class="font-semibold">257.00</span></span
          >
          <button
            class="px-5 py-2 flex items-center rounded-lg gap-2 text-white bg-blue-600"
          >
            <p>view detail</p>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="1.5rem"
              height="1.5rem"
              viewBox="0 0 24 24"
            >
              <path
                fill="none"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1.5"
                d="M4 12h16m0 0l-6-6m6 6l-6 6"
              />
            </svg>
          </button>
        </div>
      </div>

      <div
        v-for="(item, index) in 4"
        :key="index"
        class="flex px-5 py-3 border-b gap-2 lg:hidden flex-col"
      >
        <div class="flex justify-between items-center">
          <h6 class="text-purple-500 text-lg font-semibold">Airline Logo</h6>
          <span class="flex gap-2 items-center"
            ><p class="text-gray-400 text-sm">USD</p>
            <span class="font-semibold">257.00</span></span
          >
        </div>
        <button
          class="px-5 py-2 flex items-center justify-center rounded-lg gap-2 text-white bg-blue-600"
        >
          <p>view detail</p>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="1.5rem"
            height="1.5rem"
            viewBox="0 0 24 24"
          >
            <path
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M4 12h16m0 0l-6-6m6 6l-6 6"
            />
          </svg>
        </button>
      </div>
    </div>
  </UtilsModal>
  <!-- Modal end -->
  <main class="flex flex-col gap-5">
    <div
      class="rounded-[16px] bg-white p-3"
      v-for="(item, index) in props.data.flights"
      :key="item.flight_id"
    >
      <div class="flex items-center gap-8 border-b pb-4">
        <div class="flex flex-col items-center justify-center">
          <div class="flex items-center justify-center">
            <img :src="imgs[index]" class="w-10 h-10 rounded-full" alt="" />
          </div>
          <p class="text-xs text-[#938F96]">
            {{ item.outbound_group.Origin }} ,
            {{ item.outbound_group.destination }}
          </p>
        </div>
        <div>
          <div>
            <div class="flex items-center gap-2">
              <span class="font-bold">
                {{ format(item.outbound_group.departure_date_time, "HH:mm A", locale) }}
              </span>
            </div>
            <p class="text-[#7D8590] flex gap-2">
              <span>{{ item.outbound_operating_airlines[0].code }}</span>
              <span>{{
                format(item.outbound_group.departure_date_time, "D/MMM/YYYY")
              }}</span>
            </p>
          </div>
        </div>
        <div>
          <svg
            class="block mx-auto rtl:rotate-180"
            width="21"
            height="20"
            viewBox="0 0 21 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M11.6417 16.7085L13.3167 12.8168L13.6833 11.9501C13.75 11.8168 13.925 11.7001 14.075 11.7001H16.625C17.425 11.7001 18.375 11.1085 18.7417 10.3918C18.8667 10.1418 18.8667 9.8418 18.7417 9.5918C18.375 8.88346 17.4167 8.2918 16.6167 8.2918H14.0667C13.9167 8.2918 13.7417 8.17513 13.675 8.0418L11.6333 3.2918C11.4167 2.7668 10.7583 2.3418 10.1917 2.3418H9.09167C8.38333 2.3418 8.03333 2.87513 8.31667 3.53346L10.1167 7.70846C10.2583 8.03346 10.0833 8.30013 9.725 8.30013H8.8H7.3C7.10833 8.30013 6.83333 8.1918 6.7 8.05846L4.75833 6.12513C4.55833 5.92513 4.16667 5.83346 3.88333 5.92513L2.75 6.30013C2.25833 6.45013 2.025 7.00846 2.25833 7.4668L3.925 9.45013C4.18333 9.75013 4.18333 10.2418 3.925 10.5418L2.25833 12.5251C2.03333 12.9835 2.25833 13.5418 2.75 13.7085L3.88333 14.0835C4.15833 14.1751 4.55833 14.0835 4.75833 13.8835L6.7 11.9501C6.83333 11.8085 7.10833 11.7001 7.3 11.7001H9.725C10.0833 11.7001 10.25 11.9585 10.1167 12.2918L8.31667 16.4668C8.03333 17.1251 8.38333 17.6585 9.09167 17.6585H10.1917C10.7583 17.6585 11.4167 17.2335 11.6417 16.7085Z"
              fill="#605D64"
            />
          </svg>
          <p class="text-center text-xs text-[#605D64]">One stop</p>
          <p class="text-center text-xs text-[#605D64]">
            {{ item.outbound_group.destination }}
          </p>
        </div>
        <div>
          <div>
            <div class="flex items-center gap-2">
              <span class="font-bold">
                {{
                  format(
                    item.outbound_group.arrival_date_time,
                    "HH:mm A",
                    locale
                  )
                }}
              </span>
            </div>
            <p class="text-[#7D8590] flex gap-2">
            <span>  {{ item.outbound_operating_airlines[0].code }}</span>
              <span>{{ format(item.outbound_group.arrival_date_time, "D/MMM/YYYY") }}</span>
            </p>
          </div>
        </div>
      </div>
      <div
        class="mt-3 flex flex-col gap-2 lg:gap-0 lg:flex-row items-center justify-between"
      >
        <div
          class="flex justify-between w-full lg:w-auto lg:justify-start items-center gap-4"
        >
          <button
            @click="toogleModal"
            class="h-10 w-[120px] cursor-pointer rounded-lg flex items-center justify-center text-sm text-white bg-[#0A77FF]"
          >
            View Detail
          </button>
          <div class="flex items-center gap-2">
            <p class="font-bold text-[#0A77FF]">
              {{ Math.floor(item.price_detail.total_fare.payable) }}
            </p>
            <p class="text-[#7D8590]">USD</p>
          </div>
        </div>
        <div
          class="flex items-center justify-between w-full lg:w-auto gap-2 cursor-pointer font-semibold"
        >
          <p class="text-sm text-[#0A77FF]">
            {{ item.seats_remaining }} sites remined
          </p>
          <div class="flex items-center gap-2">
            <p class="text-sm text-[#605D64]">
              {{ item.outbound_group.flight_segments[0].baggage_kg }}Kg
            </p>
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M18 20V7C18 6.4477 17.5523 6 17 6H5C4.44771 6 4 6.4477 4 7V19C4 19.5523 4.44771 20 5 20H18Z"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M8 6V20"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M14 6V19"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M14 6V3C14 2.44771 13.5523 2 13 2H9C8.4477 2 8 2.44771 8 3V6"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M6.5 20V22"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
              />
              <path
                d="M16 20V22"
                stroke="#605D64"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>
            <div
              @click="toggleOpenTicket(index)"
              :class="{ 'rotate-180': isOpen[index] }"
              class="transition-all duration-500"
            >
              <svg
                width="12"
                height="7"
                viewBox="0 0 12 7"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M2.12 0.290059L6 4.17006L9.88 0.290059C10.27 -0.0999414 10.9 -0.0999414 11.29 0.290059C11.68 0.680059 11.68 1.31006 11.29 1.70006L6.7 6.29006C6.31 6.68006 5.68 6.68006 5.29 6.29006L0.700001 1.70006C0.310001 1.31006 0.310001 0.680059 0.700001 0.290059C1.09 -0.0899414 1.73 -0.0999414 2.12 0.290059Z"
                  fill="#0A77FF"
                />
              </svg>
            </div>
          </div>
        </div>
      </div>
      <TransitionExpand :duration="500">
        <div v-if="isOpen[index]" class="flex mt-5 gap-5 flex-col">
          <div class="flex flex-col">
            <h4 class="font-bold text-lg">
              {{ item.outbound_group.flight_segments[0].departure_airport }} ({{
                item.outbound_group.flight_segments[0].departure_airport
              }}) to
              {{ item.outbound_group.flight_segments[0].arrival_airport }} ({{
                item.outbound_group.flight_segments[0].arrival_airport
              }})
            </h4>
            <div class="flex text-gray-500 gap-2 items-center">
              <span>
                {{ format(item.outbound_group.departure_date_time, "HH") }}h
                {{
                  format(item.outbound_group.departure_date_time, "mm")
                }}m</span
              >
              <span>
                {{
                  format(
                    item.outbound_group.departure_date_time,
                    "ddd MMM D YYYY"
                  )
                }}</span
              >
              <!-- <span>Wed, May 10</span> -->
            </div>
          </div>
          <div class="flex px-7 py-5 rounded-xl bg-gray-100 gap-5 flex-col">
            <div class="flex items-center gap-2.5">
              <div class="flex-col items-center justify-center gap-3 flex">
                <span
                  class="stops__point_before flex relative justify-center flex-col items-center"
                ></span>
                <svg
                  class="rotate-180 text-gray-600"
                  xmlns="http://www.w3.org/2000/svg"
                  width="1.5rem"
                  height="1.5rem"
                  viewBox="0 0 48 48"
                >
                  <path
                    fill="currentColor"
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2.05"
                    d="M20.5 10.537C20.5 6.514 22.833 4.503 24 4c1.167.503 3.5 2.514 3.5 6.537v7.543L43 31v4l-16-8v9l5 8l-8-3l-8 3l5-8v-9L5 35v-4l15.5-12.92z"
                  />
                </svg>
                <span
                  class="stops__point_after flex flex-col relative items-center"
                ></span>
              </div>
              <div class="flex-col gap-3 flex">
                <div class="flex gap-2.5 items-center">
                  <span class="font-bold">{{
                    format(item.outbound_group.departure_date_time, "HH:mm")
                  }}</span>
                  <p>
                    {{
                      item.outbound_group.flight_segments[0].departure_airport
                    }}, ({{
                      item.outbound_group.flight_segments[0].departure_airport
                    }})
                  </p>
                </div>
                <p class="text-gray-500">
                  {{
                    Math.floor(
                      item.outbound_group.journey_duration_in_minute / 60
                    )
                  }}h and
                  {{
                    Math.floor(
                      item.outbound_group.journey_duration_in_minute % 60
                    )
                  }}m flight duration
                </p>
                <div class="flex gap-2.5 items-center">
                  <span class="font-bold">{{
                    format(item.outbound_group.arrival_date_time, "HH:mm")
                  }}</span>
                  <p>
                    {{
                      item.outbound_group.flight_segments[0].arrival_airport
                    }}, ({{
                      item.outbound_group.flight_segments[0].arrival_airport
                    }})
                  </p>
                </div>
              </div>
            </div>
            <div class="flex gap-2 items-center">
              <img :src="imgs[index]" class="rounded-full w-10 h-10" alt="" />
              <span>{{ item.outbound_operating_airlines[0].code }}</span>
            </div>
            <main class="text-blue-600 flex items-center">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="1.7rem"
                height="1.7rem"
                viewBox="0 0 24 24"
              >
                <path
                  fill="currentColor"
                  d="M3.385 19.385v-1h17.23v1zm1.615-3V7h4.615q0-.98.702-1.683q.702-.702 1.683-.702q.98 0 1.683.702q.702.702.702 1.683H19v9.385zm11.692-1H18V8h-1.308zM10.5 7h3q0-.65-.425-1.075T12 5.5q-.65 0-1.075.425T10.5 7m-3.192 8.385V8H6v7.385zM8.192 8v7.385h7.616V8zm-.884 7.385h.884zm9.384 0h-.884zm-9.384 0H6zm.884 0h7.616zm8.5 0H18z"
                />
              </svg>
              <span
                >2Bags ({{
                  item.outbound_group.flight_segments[0].baggage_kg
                }}
                kg)</span
              >
            </main>
          </div>
        </div>
      </TransitionExpand>
    </div>
  </main>
</template>

<script setup>
import { format } from "@formkit/tempo";
const props = defineProps(["data"]);
const { locale } = useI18n();
const isOpen = ref([]);
const toggleOpenTicket = (index) => {
  isOpen.value[index] = !isOpen.value[index];
};

const imgUrls = [];
for (const flight of props.data.flights) {
  for (const airline of flight.outbound_operating_airlines) {
    const { data } = await useFetch("/api/logo/check", {
      headers: useRequestHeaders(["cookies"]),
      query: { logo: airline.code },
    });
    imgUrls.push(URL.createObjectURL(data.value));
  }
}
const imgs = imgUrls.map((url) => url);

const modalActive = ref(false);
const toogleModal = () => {
  modalActive.value = !modalActive.value;
  document.querySelector("body").classList.add("overflow-hidden");
};
</script>
