<template>
  <div class="indexStyle__component my-5">
    <h4 class="mb-1">زبان پروژه را انتخاب کنید:</h4>
    <small class=""
      >زبان هایی که مشاهده می کنید توسط این گوینده مشاهده می شود</small
    >

    <div
      class="indexStyle__component__selectLng flex items-center justify-start gap-x-2 mt-2"
    >
      <div class="indexStyle__component__selectLng-lng">
        <i>پرچم</i>
        فارسی
      </div>
      <div class="indexStyle__component__selectLng-lng">
        <i>پرچم</i>
        فارسی
      </div>
    </div>

    <div class="mt-3 pt-3 border-t">
      <h4 class="mb-1">دسته بندی پروژه</h4>
      <small class="">
        پروژه هایی که این گوینده مایل به انجام آن نیست ، قابلیت انتخاب را
        ندارند.
      </small>
    </div>

    <div
      class="indexStyle__component__category grid grid-cols-3 md:grid-cols-6 gap-4 mt-10 mx-0 md:mx-16"
    >
      <div
        @click="toggleCategory(category.id)"
        v-for="category in categories"
        :key="category.id"
        :class="isSelected(category.id) ? 'activeCategory' : ''"
        class="indexStyle__component__category-option flex flex-col items-center justify-center py-2 cursor-pointer"
      >
        <span>{{ category.icon }}</span>
        {{ category.title }}
      </div>
    </div>

    <div class="indexStyle__component__button flex justify-end mt-10">
      <button @click="goToNext()" class="py-2 w-[50%] md:w-[20%] ">مرحله بعد</button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch, reactive } from "vue";
import { useStorPinia } from "~/stores/index";
const useData = useStorPinia();

function goToNext() {
    if( useData.componentIndex<=6){
        useData.componentIndex++;
    }
  console.log("newwwww", useData.componentIndex);
}
const selectedCategory = ref(1);
const selectedCategories = ref([1, 2]);

const toggleCategory = (categoryId) => {
  if (isSelected(categoryId)) {
    selectedCategories.value = selectedCategories.value.filter(
      (id) => id !== categoryId
    );
  } else {
    selectedCategories.value.push(categoryId);
  }
};

const isSelected = (categoryId) => {
  return selectedCategories.value.includes(categoryId);
};

const categories = reactive([
  { id: 1, title: "نریشن", icon: "icon" },
  { id: 2, title: "دوبله", icon: "icon" },
  { id: 3, title: "تلفن گویا", icon: "icon" },
  { id: 4, title: "اسلوگان", icon: "icon" },
  { id: 5, title: "کتاب صوتی", icon: "icon" },
  { id: 6, title: "تیزر تبلیغاتی", icon: "icon" },
  { id: 7, title: "موشن گرافیک", icon: "icon" },
  { id: 8, title: "پیام صوتی", icon: "icon" },
  { id: 9, title: "پادکست", icon: "icon" },
  { id: 10, title: "دکلمه", icon: "icon" },
  { id: 11, title: "تیزر رادیویی", icon: "icon" },
  { id: 12, title: "نمایش نامه", icon: "icon" },
]);
</script>
