<template>
  <section class="mt-3">
    <div class="max-w-[1248px] w-full mx-auto px-4">
      <div
        class="rounded-[24px] overflow-hidden grid sm:grid-cols-2 items-stretch"
      >
        <div class="text-white bg-[#0A77FF] p-12 px-5 sm:px-12">
          <div class="flex items-center h-full">
            <div class="h-full">
              <h1 class="font-bold text-[32px] mb-6 mt-12">
                {{ $t("nowBook.title") }}
              </h1>
              <p>
                {{ $t("nowBook.description") }}
              </p>
              <NuxtLink
                to="/"
                class="w-[143px] h-12 mt-6 rounded-lg bg-white text-sm text-[#0A77FF] flex items-center justify-center"
              >
                {{ $t("nowBook.btn") }}</NuxtLink
              >
            </div>
          </div>
        </div>
        <div>
          <img
            alt="img"
            src="/img/Frame 48097251.png"
            class="h-full"
          />
        </div>
      </div>
    </div>
  </section>
</template>
