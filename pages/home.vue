<template>
  <v-container>
    <v-card
      flat
      class="mx-auto rounded-lg"
      :max-width="$vuetify.breakpoint.mobile ? 400 : 600"
    >
      <v-card class="mx-auto rounded-lg" color="#B9F6CA">
        <v-list-item two-line>
          <v-list-item-content>
            <v-list-item-title class="text-h5">
              Halo NandaRusfikri!
            </v-list-item-title>
            <v-list-item-subtitle
              >Kamu telah menghemat uang sebanyak</v-list-item-subtitle
            >
          </v-list-item-content>
        </v-list-item>

        <v-card flat color="#B9F6CA">
          <v-card-subtitle class="py-0">Tabungan kamu</v-card-subtitle>
          <v-card-subtitle class="py-0 text-h3">
            19.456.123
          </v-card-subtitle>
          <v-card-actions>
            <v-btn outlined small>
              <v-icon small>mdi-plus</v-icon>Isi Saldo</v-btn
            ></v-card-actions
          >
        </v-card>
      </v-card>
      <v-toolbar dense flat>
        <v-toolbar-title>Riwayat Tabungan </v-toolbar-title>
      </v-toolbar>
      <v-list>
        <v-list-item three-line v-for="item in tabungan" :key="item.date">
          <v-list-item-content>
            <v-list-item-title> <b>Rp{{item.price}}</b></v-list-item-title>
            <v-list-item-subtitle>
              {{item.date}}
            </v-list-item-subtitle>
            <v-list-item-subtitle>
              {{item.note}}
            </v-list-item-subtitle>
          </v-list-item-content>
          <v-list-item-action>
            <v-btn text small color="primary">
              <strong>  {{item.status}}</strong>
            </v-btn>
          </v-list-item-action>
        </v-list-item>
      </v-list>

      <!-- <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-cloud-download</v-icon>
        </v-list-item-icon>
        <v-list-item-subtitle>48%</v-list-item-subtitle>
      </v-list-item> -->

      <!-- <v-slider
        v-model="time"
        :max="6"
        :tick-labels="labels"
        class="mx-4"
        ticks
      ></v-slider> -->

      <!-- <v-list class="transparent">
        <v-list-item v-for="item in forecast" :key="item.day">
          <v-list-item-title>{{ item.day }}</v-list-item-title>

          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-subtitle class="text-right">
            {{ item.temp }}
          </v-list-item-subtitle>
        </v-list-item>
      </v-list> -->

      <v-divider></v-divider>

      <v-card-actions>
        <v-btn text>
          Full Report
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      labels: ["SU", "MO", "TU", "WED", "TH", "FR", "SA"],
      time: 0,
      tabungan: [
        { price: 100000, date: "9 July 2021", note: "bulanan", status: "berhasil" },
        { price: 100000, date: "8 July 2021", note: "bulanan", status: "berhasil"},
        { price: 100000, date: "3 July 2021", note: "bulanan",status: "berhasil" },
        { price: 100000, date: "1 July 2021", note: "bulanan",status: "berhasil" }
      ],
      forecast: [
        {
          day: "Tuesday",
          icon: "mdi-white-balance-sunny",
          temp: "24\xB0/12\xB0"
        },
        {
          day: "Wednesday",
          icon: "mdi-white-balance-sunny",
          temp: "22\xB0/14\xB0"
        },
        { day: "Thursday", icon: "mdi-cloud", temp: "25\xB0/15\xB0" }
      ]
    };
  }
};
</script>
<style scoped>
#latar {
  background: rgb(0, 199, 166);
  background: radial-gradient(
    circle,
    rgba(0, 199, 166, 0.46589057986475846) 0%,
    rgba(0, 199, 166, 1) 100%
  );
}
</style>
