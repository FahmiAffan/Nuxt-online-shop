<template>
  <div>
    <v-app-bar color="#03A9F4" class="navbars" height="80" dense dark>
      <v-app-bar-nav-icon @click.stop="sideBar = !sideBar"></v-app-bar-nav-icon>

      <v-toolbar-title>Page title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <NuxtLink to="/cart">
          <v-icon color="white">mdi-cart</v-icon>
        </NuxtLink>
      </v-btn>
    </v-app-bar>
    <v-card width="256">
      <v-navigation-drawer v-model="sideBar" app temporary>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6"> Application </v-list-item-title>
            <v-list-item-subtitle> subtext </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list dense nav>
          <v-list-item link>
            <v-list-item-icon> </v-list-item-icon>

            <v-list-item-content> </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'AppbarComponents',
  data() {
    return {
      sideBar: false,
    }
  },
  mounted() {
    console.log(this.$route.name)
  },
  // eslint-disable-next-line
}
</script>

<style>
.absolute {
  position: fixed;
}
.navbars {
  position: relative;
  z-index: 1;
}
</style>
