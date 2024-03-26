<template>
  <nav
    class="navbarStyle w-full flex items-center justify-between h-[7%] md:h-[10%] bg-white shadow-gray-400 px-5 md:px-16"
  >
    <div class="flex md:hidden">
      <i class="icon-menu"></i>
    </div>

    <nuxt-link class="navbarStyle__logo" to="/">
      <i class="icon-vodafone"></i>
    </nuxt-link>

    <div class="flex md:hidden">profile</div>

    <ul class="hidden md:flex items-center justify-between gap-x-6">
      <li v-for="menu in menus" :key="menu.id">
        <nuxt-link :to="menu.link">
          {{ menu.name }}
        </nuxt-link>
      </li>
    </ul>

    <div
      class="navbarStyle__buttons hidden md:flex items-center justify-between gap-x-3"
    >
      <!-- select for change lng  -->
      <div class="navbarStyle__buttons__lng">
        فارسی
        <i>پرچم</i>

    </div>

      <nuxt-link class="navbarStyle__buttons__panel flex items-center justify-center" to="/">پنل گویندکان</nuxt-link>

      <div class="navbarStyle__buttons__authBtn flex items-center justify-center">
        <nuxt-link to="/">ورود</nuxt-link>
        &nbsp;/&nbsp;
        <nuxt-link to="/">عضویت</nuxt-link>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, computed, onMounted, watch, reactive } from "vue";
const menus = ref([
  { id: 1, name: "صفحه اصلی", link: "/" },
  { id: 2, name: " خدمات بانک صدا", link: "/" },
  { id: 3, name: " لیست گویندگان", link: "/" },
  { id: 4, name: "دانلود صدا ", link: "/" },
  { id: 5, name: " ارتباط با ما ", link: "/" },
]);
</script>
