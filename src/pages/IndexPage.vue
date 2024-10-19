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
import { onMounted, ref, watch } from "vue";
import { QSpinnerGears, useQuasar } from "quasar";

const undergraduatedDegree = ref(null);
const $q = useQuasar();
let costs = ref(100);
const options = [
  "Undergraduate degree",
  "College degree",
  "High school degree",
  "Middle school degree",
];
onMounted(() => {
  // countCosts();
});
watch(
  () => undergraduatedDegree.value,
  (newVal) => {
    // console.log(newVal);
    $q.notify({
      message: `Degree: ${newVal}`,
    });
    countCosts(newVal, null);
  }
);

const countCosts = (degree, familyWorth) => {
  // console.log(degree, familyWorth);
  let count;
  if (degree == "Undergraduate degree") {
    count = costs.value * 1.5;
  } else if (degree == "College degree") {
    count = costs.value * 1.2;
  } else if (degree === "High school degree") {
    count = costs.value * 1.05;
  } else if (degree == "Middle school degree") {
    count = costs.value * 0.9;
  }
  console.log(count);
};
</script>

<style></style>
