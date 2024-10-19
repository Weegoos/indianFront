<template>
  <div>
    <q-select
      label="Jump up"
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
const options = ["Google", "Facebook", "Twitter", "Apple", "Oracle"];
watch(
  () => undergraduatedDegree.value,
  (newVal) => {
    console.log(newVal);
  }
);
</script>

<style></style>
