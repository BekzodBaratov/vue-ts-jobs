<template>
  <div class="app flex items-center justify-center mt-4">
    <div class="w-3/4 space-y-4">
      <header class="flex justify-center gap-4">
        <button
          class="py-1 px-6 rounded-md bg-blue-300 text-white capitalize border-4 border-blue-500 active:bg-blue-400"
          @click="handleClick('title')"
        >
          order by title
        </button>
        <button
          class="py-1 px-6 rounded-md bg-blue-300 text-white capitalize border-4 border-blue-500 active:bg-blue-400"
          @click="handleClick('salary')"
        >
          order by salary
        </button>
        <button
          class="py-1 px-6 rounded-md bg-blue-300 text-white capitalize border-4 border-blue-500 active:bg-blue-400"
          @click="handleClick('location')"
        >
          order by location
        </button>
      </header>
      <JobsList :jobs="jobs" :order="order" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

import JobsList from "./components/JobsList.vue";

import "@/assets/global.css";
import Job from "@/types/Job";
import OrderTerm from "./types/OrderTerm";

const jobs = ref<Job[]>([
  { title: "Front-end developer", location: "tashkent", salary: 4000000, id: "1" },
  { title: "System admin", location: "jizzax", salary: 3500000, id: "2" },
  { title: "Data since", location: "navoiy", salary: 2100000, id: "3" },
  { title: "back-end developer", location: "andijon", salary: 2500000, id: "4" },
  { title: "back-end developer", location: "namangan", salary: 4500000, id: "5" },
  { title: "back-end developer", location: "buxoro", salary: 5000000, id: "6" },
  { title: "back-end developer", location: "jizzax", salary: 1500000, id: "7" },
]);

const order = ref<OrderTerm>("title");

const handleClick = (term: OrderTerm) => {
  order.value = term;
};

console.log(jobs);
</script>
