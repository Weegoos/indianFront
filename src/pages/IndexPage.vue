<template>
  <div class="q-pa-lg">
    <q-select
      label="Degree"
      transition-show="jump-up"
      transition-hide="jump-up"
      filled
      v-model="undergraduatedDegree"
      :options="options"
      style="width: 250px"
      class="q-mb-md"
    />
    <q-select
      label="Family Worth"
      transition-show="jump-up"
      transition-hide="jump-up"
      filled
      v-model="familytWorth"
      :options="familyOptions"
      style="width: 250px"
      class="q-mb-md"
    />
    <q-select
      label="Caste"
      transition-show="jump-up"
      transition-hide="jump-up"
      filled
      v-model="caste"
      :options="casteOptions"
      style="width: 250px"
      class="q-mb-md"
    />
    <q-checkbox dense v-model="teal" label="Teal" color="teal" /> <br />
    <q-btn dense no-caps label="Посчитать" @click="getResult" />
  </div>
</template>

<script setup>
import { onMounted, ref, watch } from "vue";
import { QSpinnerGears, useQuasar } from "quasar";

const undergraduatedDegree = ref(null);
const $q = useQuasar();
let costs = ref(100);
const caste = ref("");
const teal = ref("");
const options = [
  "Undergraduate degree",
  "College degree",
  "High school degree",
  "Middle school degree",
];

const familytWorth = ref(null);
const familyOptions = [
  "Between 5,000$ and 10,000$",
  "More than 10,000$",
  "Less than 5,000$",
];

const casteOptions = [
  "Brahmin",
  "Kshatriya",
  "Vaishya",
  "Shudra",
  "Varna - untouchable",
];
onMounted(() => {
  // countCosts();
});

const getResult = () => {
  countCosts(undergraduatedDegree.value, null);
};

const countCosts = (familyWorth) => {
  // console.log(degree, familyWorth);
  let count;
  if (undergraduatedDegree.value == "Undergraduate degree") {
    costs.value = costs.value * 1.5;
  } else if (undergraduatedDegree.value == "College degree") {
    costs.value = costs.value * 1.2;
  } else if (undergraduatedDegree.value === "High school degree") {
    costs.value = costs.value * 1.05;
  } else if (undergraduatedDegree.value == "Middle school degree") {
    costs.value = costs.value * 0.9;
  } else {
    throw new Error("Вы не выбрали степень образование");
  }
  // console.log(costs.value);
  countWorth(costs.value);
};

const countWorth = (degreeCount) => {
  // console.log(degreeCount);
  if (familytWorth.value === "Less than 5,000$") {
    costs.value = degreeCount * 1.2;
  } else if (familytWorth.value === "Between 5,000$ and 10,000$") {
    costs.value = degreeCount * 1.5;
  } else if (familytWorth.value === "More than 10,000$") {
    costs.value = degreeCount * 2;
  }
  // console.log(costs.value);
  countCaste(costs.value);
};

const countCaste = (degreeCount) => {
  if (caste.value === "Brahmin") {
    costs.value = degreeCount + 100;
  } else if (caste.value === "Kshatriya") {
    costs.value = degreeCount + 50;
  } else if (caste.value === "Vaishya") {
    costs.value = degreeCount + 20;
  } else if (caste.value === "Shudra") {
    costs.value = degreeCount + 10;
  } else if (caste.value === "Varna - untouchable") {
    costs.value = degreeCount - 50;
  }

  console.log(costs.value);
};
</script>

<style></style>
