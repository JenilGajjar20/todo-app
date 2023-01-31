<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="justify-between">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
        <p class="no-margin text-subtitle2 text-grey-3">v {{ version }}</p>
      </q-toolbar>
      <div class="q-px-lg">
        <div class="text-h4 text-weight-medium">Todo App</div>
        <p class="text-subtitle2">{{ currentDate }}</p>
      </div>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="200"
      :breakpoint="600"
    >
      <q-scroll-area
        style="
          height: calc(100% - 165px);
          margin-top: 165px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section> Tasks </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="../assets/img/user.jpg" />
          </q-avatar>
          <div class="text-weight-bold">Jenil Gajjar</div>
          <div>Frontend Developer</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from "quasar";
import { version } from "../../package.json";

export default {
  name: "MainLayout",
  data() {
    return {
      leftDrawerOpen: false,
      version,
    };
  },
  computed: {
    currentDate() {
      let timestamp = Date.now();
      return date.formatDate(timestamp, "dddd, Do MMM");
    },
  },
};
</script>
