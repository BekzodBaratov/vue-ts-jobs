<template>
  <div>
    <p class="font-semibold text-lg text-blue-400 mb-3 capitalize">ordered by {{ order }}</p>
    <ul class="space-y-4 mb-6">
      <li class="bg-white py-4 px-6 rounded-md" v-for="job in OrderedJobs" :key="job.id">
        <h2 class="text-2xl font-bold mb-3">{{ job.title }} in {{ job.location }}</h2>
        <div class="">
          <p class="text-green-600 font-semibold mb-2">{{ job.salary }} so'm</p>
        </div>
        <div class="decr">
          <p class="">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Consequatur soluta rem expedita, aperiam dicta eos
            cupiditate. Porro ipsum beatae, ducimus, nemo nam perferendis mollitia consequuntur fugiat doloribus
            provident, sint quisquam?
          </p>
        </div>
      </li>
      <li
        class="flex items-center justify-center bg-white px-6 rounded-md border-4 text-5xl text-gray-700 border-gray-400 py-12 hover:bg-gray-200 active:bg-gray-300 cursor-pointer"
      >
        +
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { computed, defineProps, PropType } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

const props = defineProps({
  jobs: { type: Array as PropType<Job[]>, required: true },
  order: { type: String as PropType<OrderTerm>, required: true },
});

const OrderedJobs = computed(() => {
  return [...props.jobs].sort((a: Job, b: Job) => {
    return a[props.order] > b[props.order] ? 1 : -1;
  });
});

console.log(props);
</script>
