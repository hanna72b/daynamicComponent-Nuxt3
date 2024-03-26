<template>
  <div class="indexStyle mx-4 md:mx-32 mt-4">
    <!-- change component column desktop-->
    <div
      class="indexStyle__col px-6 py-2 relative hidden md:flex flex-col items-center"
    >
      <div
        class="indexStyle__col__numbers w-[89%] flex items-center justify-between absolute"
      >
        <span
          @click="useData.componentIndex = number"
          v-for="(number, index) in numbers"
          :key="index"
          :class="useData.componentIndex === number ? 'activeOption' : ''"
          class="rounded-full cursor-pointer"
        >
          {{ number }}
        </span>
      </div>

      <div
        class="indexStyle__col__border w-[89%] flex items-center justify-between pt-4 mt-4 mx-7"
      ></div>

      <div
        class="indexStyle__col__text w-full flex items-center justify-between mt-3"
      >
        <span
          @click="useData.componentIndex = option.id"
          v-for="option in options"
          :key="option.id"
          class="cursor-pointer"
          :class="useData.componentIndex === option.id ? 'activeOption' : ''"
        >
          {{ option.text }}</span
        >
      </div>
    </div>

    <!-- change component column mpbile-->
    <div class="indexStyle__col p-3 flex items-center gap-x-2 md:hidden">
      <div class="indexStyle__col__numbersForMobile">
        <span class="rounded-full">
          {{ options[useData.componentIndex - 1].id }}</span
        >
      </div>

      <div class="indexStyle__col__textForMobile flex flex-col">
        {{ options[useData.componentIndex - 1].text }}
        <small>مرحله {{ options[useData.componentIndex - 1].id }} از 6 </small>
      </div>
    </div>

    <!-- dynamic component  -->
    <component :is="selectedComponent" />
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch } from "vue";
import { useStorPinia } from "~/stores/index";
const useData = useStorPinia();

const numbers = reactive([1, 2, 3, 4, 5, 6]);
const options = reactive([
  { id: 1, text: "زبان و نوع پروژه" },
  { id: 2, text: "   متن پروژه" },
  { id: 3, text: " جزئیات پروژه  " },
  { id: 4, text: "پرداخت هزینه   " },
  { id: 5, text: "ضبط پروژه " },
  { id: 6, text: "  دانلود فایل پروژه " },
]);

// const componentIndex = ref(1);

const lang = resolveComponent("projectOptions-lng");
const text = resolveComponent("projectOptions-text");
const details = resolveComponent("projectOptions-details");
const pay = resolveComponent("projectOptions-pay");
const recording = resolveComponent("projectOptions-recording");
const download = resolveComponent("projectOptions-download");

const selectedComponent = computed(() => {
  switch (useData.componentIndex) {
    case 1:
      return lang;
    case 2:
      return text;
    case 3:
      return details;
    case 4:
      return pay;
    case 5:
      return recording;
    case 6:
      return download;
    default:
      return lang;
  }
});
</script>
