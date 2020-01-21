<template>
  <v-app id="noonoo">
    <div>
      <v-app-bar color="light-blue darken-1" collapse-on-scroll class="justify-center"  height="80px">
        <v-spacer />
        <v-toolbar-title>
          <router-link to="/">
            <img src="/logo.png" width="240" height="45" alt="Logo Noo-Noo" />
          </router-link>
        </v-toolbar-title>
        <v-img src="/noonoo.gif" class="ml-4" max-width="75" max-height="85" />
        <v-spacer />
      </v-app-bar>
    </div>

    <v-content>
      <router-view>
        <v-container></v-container>
      </router-view>
    </v-content>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String
  },
  data: () => ({
    drawer: null
  })
};
</script>
