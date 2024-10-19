<template>
  <div>
    <q-select
      label="Degree"
      transition-show="jump-up"
      transition-hide="jump-up"
      filled
      v-model="undergraduatedDegree"
      :options="options"
      style="width: 250px"
    />
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const undergraduatedDegree = ref(null);
const options = [
  "Undergraduate degree ",
  "College degree ",
  "High school degree",
  "Middle school degree ",
];
watch(
  () => undergraduatedDegree.value,
  (newVal) => {
    console.log(newVal);
  }
);
</script>

<style></style>
