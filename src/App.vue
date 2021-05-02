<template>
  <v-app>
    <!-- navigation drawer -->
    <v-navigation-drawer v-model="drawer" app clipped>
      <v-list-item
        v-for="item in items"
        :key="item.title"
        link
        :to="{ name: item.routerName }"
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-navigation-drawer>
    <!-- navigation drawer -->

    <!-- app bar -->
    <v-app-bar color="primary" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer">
        <v-icon large>
          {{ drawer ? 'mdi-chevron-left' : 'mdi-chevron-right' }}
        </v-icon>
      </v-app-bar-nav-icon>

      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
      </div>

      <v-toolbar-title> Idea Playground </v-toolbar-title>
    </v-app-bar>
    <!-- app bar -->

    <v-main>
      <!-- Provides the application the proper gutter -->
        <transition name="fade" mode="out-in">
          <router-view />
        </transition>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
    // HelloWorld,
  },

  data: () => ({
    drawer: null,
    items: [
      {
        title: '작업환경 초기화',
        icon: 'mdi-view-dashboard',
        routerName: 'InitNamespace',
      },
      { title: 'About', icon: 'mdi-forum', routerName: 'About' },
    ],
  }),
};
</script>

<style>
/* google fonts */
@import url('https://fonts.googleapis.com/css2?family=Nanum+Gothic:wght@400;700&family=Noto+Sans+KR&family=Roboto&display=swap');

/* html,
body {
  font-family: 'Noto Sans KR', 'Nanum Gothic', 'Roboto', sans-serif;
} */

#app {
  font-family: 'Roboto', 'Noto Sans KR', 'Nanum Gothic', sans-serif;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
