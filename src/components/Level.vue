<template>
                <!-- Fan speed -->
                <v-card class="mx-auto rounded-xl" max-width="600" >
              <v-toolbar flat dense>
                <v-toolbar-title>
                  <span class="subheading grey--text">Fan speed</span>
                </v-toolbar-title>
                <v-spacer></v-spacer>
                <v-icon color="grey" small>fas fa-hot-tub</v-icon>
                <span class="ml-2 caption grey--text">Swing</span>
                <v-switch
                  color="green"
                  v-model="on"
                  class="mt-5 ml-2"
                  @click="swing"
                ></v-switch>
                <!-- <v-btn icon>
          <v-icon>mdi-share-variant</v-icon>
        </v-btn> -->
              </v-toolbar>

              <v-card-text>
                <v-row class="mb-4" justify="space-between">
                  <v-col class="text-left">
                    <span class="text-h4 font-weight-light" v-text="bpm"></span>
                    <span class="subheading font-weight-light mr-1">LEVEL</span>
                   
                  </v-col>
                </v-row>

                <v-slider
                  v-model="bpm"
                  :color="color"
                  track-color="grey"
                  always-dirty
                  min="1"
                  max="5"
                >
                  <template v-slot:prepend>
                    <v-icon :color="color" @click="decrement(fanDec())">
                      mdi-minus
                    </v-icon>
                  </template>

                  <template v-slot:append>
                    <v-icon :color="color" @click="increment(fanInc())">
                      mdi-plus
                    </v-icon>
                  </template>
                </v-slider>
              </v-card-text>
            </v-card>
</template>
<script>
// @ is an alias to /src



export default {
  name: "Home",
  data: () => ({
    bpm: 1,
    interval: null,

    
  }),
  computed: {
    color() {
      if (this.bpm < 6) return "indigo";
      return "indigo";
    },
  },

  methods: {
    decrement() {
      this.bpm--;
    },
    increment() {
      this.bpm++;
    },
    toggle() {
      this.isPlaying = !this.isPlaying;
    },

    fanDec() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg=&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
        request: this.bpm-1,
        
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };
      fetch(
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Fan?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    fanInc() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg=&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
        request: this.bpm+1,
        
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };
      fetch(
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Fan?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    swing() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg=&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
      
        
      });
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };
      fetch(
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Swing?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },

  },
};
</script>