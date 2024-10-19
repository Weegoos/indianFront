<template>
  <div>
    <q-layout view="hHr LpR lFf" container style="height: 100vh">
      <q-header reveal elevated>
        <q-toolbar class="bg-white" style="color: black">
          <q-btn flat round dense icon="assignment_ind" />
          <q-toolbar-title> Indian </q-toolbar-title>
          <!-- <q-btn flat round dense icon="apps" class="q-mr-xs" /> -->
          <!-- <q-btn flat round dense icon="more_vert" /> -->
        </q-toolbar>
      </q-header>
      <q-page-container>
        <q-page>
          <router-view />
        </q-page>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
