<template>
  <!-- <router-view /> -->
  <div>
    <AppLayout />
  </div>
</template>

<script setup>
import { useQuasar } from "quasar";
import { onErrorCaptured } from "vue";
import AppLayout from "./layouts/AppLayout.vue";
defineOptions({
  name: "App",
});

const $q = useQuasar();

onErrorCaptured((err, instance, info) => {
  $q.notify({
    message: `${info}, ${err}`,
    color: "negative",
    icon: "error",
  });
});
</script>
