<template>
  <q-layout view="hHh LpR fFf" class="bg-blue-grey-1">
    <q-header elevated class="bg-pink-ieen">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Computos </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <div class="text-center q-pa-md">
          <q-img src="../assets/Conoceles2@300x.png" />
        </div>
        <div class="text-weight-bold text-black q-pa-md">
          <br />
          Bienvenido(a) {{ userName }}
        </div>

        <q-item
          clickable
          v-ripple
          class="text-grey-8"
          :to="{ name: 'inicio' }"
          active-class="text-pink-ieen-1"
        >
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section> Inicio </q-item-section>
        </q-item>
        <q-item
          clickable
          v-ripple
          class="text-grey-8"
          :to="{ name: 'captura' }"
          active-class="text-pink-ieen-1"
        >
          <q-item-section avatar>
            <q-icon name="edit_square" />
          </q-item-section>
          <q-item-section> Captura </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
54545;
const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
<style lang="scss">
.bg-pink-ieen {
  color: white;
  background: #d1308a !important;
}
</style>
