<template>
  <v-app app>
    <v-app-bar color="white" flat>
      <v-toolbar-title>Buahati</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn outlined>
        Daftar
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-snackbar
        v-model="snackbar.enabled"
        :color="snackbar.color"
        absolute
        top
      >
        <strong>{{ snackbar.message }}</strong>
        <template v-slot:action="{ attrs }">
          <v-btn dark icon v-bind="attrs" @click="snackbar.enabled = false">
            <v-icon dark>mdi-close</v-icon>
          </v-btn>
        </template>
      </v-snackbar>
      <nuxt />
    </v-main>
  </v-app>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? "dark" : "light";
    },
    snackbar() {
      return this.$store.getters.Snackbar;
    }
  }
};
</script>
<style scoped></style>
