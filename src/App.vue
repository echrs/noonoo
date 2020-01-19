<template>
  <v-app id="fibot">
    <div>
      <v-app-bar color="blue" class="justify-center" flat height="75px">
        <v-spacer />
        <v-toolbar-title>
          <router-link to="/">
            <img src="/logo.png" width="150" height="30" alt="Logo Noo-Noo" />
          </router-link>
        </v-toolbar-title>
        <v-img src="/noonoo.gif" class="ml-3" max-width="75" max-height="75" />
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
