<template>
  <v-ons-page id="app">
    <v-ons-splitter>
      <v-ons-splitter-side swipeable collapse width="250px"
        :animation="$ons.platform.isAndroid() ? 'overlay' : 'reveal'"
        :open.sync="menuIsOpen">
        <menu-page></menu-page>
      </v-ons-splitter-side>

      <v-ons-splitter-content>
        <home-page></home-page>
      </v-ons-splitter-content>
    </v-ons-splitter>
  </v-ons-page>
</template>

<script>
import HomePage from "./pages/HomePage";
import MenuPage from "./pages/MenuPage";

export default {
  name: "app",
  computed: {
    menuIsOpen: {
      get() {
        return this.$store.state.splitter.open;
      },
      set(newValue) {
        this.$store.commit("splitter/toggle", newValue);
      }
    }
  },
  components: {
    HomePage,
    MenuPage
  }
};
</script>

<style>
ons-splitter-side[side="left"][animation="overlay"] {
  border-right: 1px solid #bbb;
}
.page__content {
  background-color: #146eb4 !important;
}
.toolbar + .page__background + .page__content {
  top: 10px;
}
</style>
