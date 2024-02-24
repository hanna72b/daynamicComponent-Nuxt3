<template>
  <div
    class="navbarStyle w-full flex md:hidden items-center justify-between h-[7%] md:h-[10%] bg-white shadow-gray-400 px-5 md:px-16"
  >
    <ul class=" w-full flex items-center justify-around gap-x-6">
      <li v-for="menu in fixedMenus" :key="menu.id">
        <nuxt-link class="text-black" :to="menu.link">
          {{ menu.name }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch, reactive } from "vue";
const fixedMenus = ref([
  { id: 1, name: " خانه", link: "/" },
  { id: 2, name: "گویندگان", link: "/" },
  { id: 3, name: " ذخیره ها", link: "/" },
  { id: 4, name: " حساب کاربری ", link: "/" },
]);
</script>
