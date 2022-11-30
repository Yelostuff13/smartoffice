<template>
  <v-row justify="center" class="space px-1">
    <v-col
      cols="12"
      xs="12"
      sm="6"
      md="4"
      v-for="(product, i) in products"
      :key="i"
    >
      <v-card-title
        class="justify-center grey--text text-grey-darken-1 caption mt-n3"
        >{{ product.title }}</v-card-title
      >

      <v-card-actions class="mx-2 mt-n4">
        <v-btn outlined class="mt-n2 add">
          <v-icon color="indigo" @click="decrement(tempDec())">
            mdi-minus
          </v-icon>
        </v-btn>
        <v-spacer></v-spacer>
        <strong class="text-h3 mx-2" v-text="bpm"></strong>
        <v-spacer></v-spacer>
        <v-btn outlined class="mt-n2 add">
          <v-icon color="indigo" @click="increment(tempInc())">
            mdi-plus
          </v-icon>
        </v-btn>
      </v-card-actions>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    bpm: 25,
    products: [{ img: "air-conditioner2.png", title: "Temperature" }],
  }),
  methods: {
    decrement() {
      this.bpm--;
    },
    increment() {
      this.bpm++;
    },
    tempDec() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg=&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
        request: this.bpm - 1,
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };
      fetch(
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Temp?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    tempInc() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg=&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
        request: this.bpm + 1,
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };
      fetch(
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Temp?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
  },
};
</script>

<style>
</style>