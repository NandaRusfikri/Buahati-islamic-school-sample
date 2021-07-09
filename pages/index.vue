<template>
  <v-app app :style="{ background: $vuetify.theme.themes[theme].background }">
    <v-row align="center" justify="center">
      <v-col class="px-5" cols="12" md="5" sm="12">
        <v-card class="rounded-lg " hover :loading="loading">

          <div class="pt-5 text-h4 text-center">
            Hai!
          </div>
          <p class="text-center px-2">
            Silakan masuk dan mulai menabung antar bank tanpa biaya hari ini
          </p>

          <v-card-text>
            <v-form>
              <v-text-field
                outlined
                flat
                label="Email"
                placeholder="Email"
                persistent-hint
                name="Email"
                v-model="email"
                :rules="emailRules"
                prepend-inner-icon="mdi-email"
                type="text"
              />

              <v-text-field
                :append-icon="show4 ? 'mdi-eye' : 'mdi-eye-off'"
                prepend-inner-icon="mdi-key"
                :rules="passRules"
                :type="show4 ? 'text' : 'password'"
                name="password"
                label="Password"
                outlined
                v-model="password"
                @click:append="show4 = !show4"
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn
              class="rounded-lg"
              block
              color="primary"
              :disabled="loading"
              dark
              large
              @click="Login"
              >Sign In</v-btn
            >
            <v-spacer />
          </v-card-actions>
          <v-card-actions>
            <v-btn class="caption" @click="FuncForgetPassowrd()" text
              >Forget Password?</v-btn
            >
            <v-spacer />
            <v-btn class="caption" @click="FuncRegister()" text
              >Create New Account</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
export default {
  middleware({ store, redirect, app }) {
    // if (app.$cookies.get("mahasiswa") !== undefined) {
    //   return redirect("/biodata");
    // }
  },
  name: "login",
  layout: "blank",
  data() {
    return {
      mahasiswa: [
        {
          email: 201943502024,
          password: 201943502024,
          nama: "Sindy Silvya"
        },

        {
          email: 201943502022,
          password: 201943502022,
          nama: "Rendi Gunawan"
        },
        {
          email: "admin@buahati.com",
          password: 12345678,
          nama: "NandaRusfikri"
        },

        {
          email: 201943502005,
          password: 201943502005,
          nama: "Lani Oktofiyanto"
        }
      ],
      show4: false,
      loading: false,

      email: null,
      password: null,
      color: { snackbar: "" },
      snackbar: false,
      message: null,
      response: null,
      emailRules: [v => !!v || "email wajib diisi"],
      passRules: [v => !!v || "Password wajib diisi"]
    };
  },
  mounted() {},

  methods: {
    FuncForgetPassowrd() {
      let snackbar = {
        color: "warning",
        message: "Password Sama Dengan email",
        enabled: true
      };

      this.$store.commit("SET_SNACKBAR", snackbar);
    },
    FuncRegister() {
      console.log("ayams");
      this.$router.push("/register");
    },

    async Login({ commit }) {
      this.loading = true;

      var exist = null;
      for (let i = 0; i < this.mahasiswa.length; i++) {
        if (this.mahasiswa[i].email == this.email) {
          exist = i;
        }
      }

      if (exist == null) {
        let snackbar = {
          color: "error",
          message: "email tidak ada",
          enabled: true
        };

        this.$store.commit("SET_SNACKBAR", snackbar);
      } else if (
        exist !== null &&
        this.mahasiswa[exist].email == this.email &&
        this.mahasiswa[exist].email == this.password
      ) {
        this.$cookies.set("mahasiswa", this.mahasiswa[exist]);
        this.$store.commit("SET_USER", this.mahasiswa[exist]);
        this.$router.push("/home");
      } else {
        let snackbar = {
          color: "warning",
          message: "password salah",
          enabled: true
        };

        this.$store.commit("SET_SNACKBAR", snackbar);
      }

      this.loading = false;
    }
  },
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? "dark" : "light";
    }
  }
};
</script>
<style scoped>
.rounded-card {
  border-radius: 18px;
}
.rounded-btn {
  border-radius: 10px;
}
</style>
