<template>
  <div
    class="w-full h-screen overflow-y-hidden flex flex-col justify-between md:justify-start text-base md:text-xs"
  >
    <navbar />

    <div @click="$router.back()" class="mt-4 ps-5 md:ps-16 cursor-pointer">
      <i class="icon-redo2"></i>
      بازگشت
      <!-- test  -->
    </div>
    <slot />
    <fixedNavbar />
  </div>
</template>

<script setup></script>
