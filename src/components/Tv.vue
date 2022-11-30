<template>
  <v-item-group mandatory class="mt-n1">
    <v-container>
      <v-row justify="center" class="space">
        <v-col cols="12" xs="5" sm="4" md="2">

          <div class="text-center">

            <v-btn class="ma-2" outlined flat height="80" color="#2053BF"  @click="source()">
              <!-- <v-img max-height="40" max-width="40" src="hdmi-port.png"></v-img> -->
              <v-row>
                <v-col cols="12" sm="12">
                  <v-list-item three-line class="text-center">
                    <v-list-item-content>
                      <div align="center" justify="center">
                        <v-img max-height="40" max-width="40" src="hdmi-port.png"></v-img>
                      </div>
                      <v-list-item-subtitle
                        :class="active ? 'green--text' : 'black--text'"
                        class="caption mt-4"
                        >INPUT</v-list-item-subtitle
                      >
                    </v-list-item-content>
                  </v-list-item>
              </v-col>
              </v-row>
            </v-btn>

            <v-btn class="ma-2" outlined flat height="80" color="#2053BF"  @click="exit()">
              <!-- <v-img max-height="40" max-width="40" src="hdmi-port.png"></v-img> -->
              <v-row>
                <v-col cols="12" sm="12">
                  <v-list-item three-line class="text-center">
                    <v-list-item-content>
                      <div align="center" justify="center">
                        <v-img max-height="40" max-width="40" src="exit1.png"></v-img>
                      </div>
                      <v-list-item-subtitle
                        :class="active ? 'green--text' : 'black--text'"
                        class="caption mt-4"
                        >EXIT⠀ </v-list-item-subtitle
                      >
                    </v-list-item-content>
                  </v-list-item>
              </v-col>
              </v-row>
            </v-btn>
            <v-btn class="ma-2" outlined flat height="80" color="#2053BF"  @click="VolumeDown()">
              <!-- <v-img max-height="40" max-width="40" src="hdmi-port.png"></v-img> -->
              <v-row>
                <v-col cols="12" sm="12">
                  <v-list-item three-line class="text-center">
                    <v-list-item-content>
                      <div align="center" justify="center">
                        <v-img max-height="40" max-width="40" src="volume-down1.png"></v-img>
                      </div>
                      <v-list-item-subtitle
                        :class="active ? 'green--text' : 'black--text'"
                        class="caption mt-4"
                        >DOWN</v-list-item-subtitle
                      >
                    </v-list-item-content>
                  </v-list-item>
              </v-col>
              </v-row>
            </v-btn>
            <v-btn class="ma-2" outlined flat height="80" color="#2053BF"  @click="VolumeUp()">
              <!-- <v-img max-height="40" max-width="40" src="hdmi-port.png"></v-img> -->
              <v-row>
                <v-col cols="12" sm="12">
                  <v-list-item three-line class="text-center">
                    <v-list-item-content>
                      <div align="center" justify="center">
                        <v-img max-height="40" max-width="40" src="volume-up1.png"></v-img>
                      </div>
                      <v-list-item-subtitle
                        :class="active ? 'green--text' : 'black--text'"
                        class="caption mt-4"
                        >⠀UP⠀ </v-list-item-subtitle
                      >
                    </v-list-item-content>
                  </v-list-item>
              </v-col>
              </v-row>
            </v-btn>  
          </div>
          
        </v-col>
      </v-row>
    </v-container>
  </v-item-group>
</template>

<script>
export default {
  data: () => ({
    temp: [
      { img: "hdmi-port.png", title: "INPUT" },
      { img: "exit1.png", title: "EXIT" },
      { img: "volume-down1.png", title: "VOLUME DOWN" },
      { img: "volume-up1.png", title: "VOLUME UP" },
    ],
  }),

  methods: {
    source() {
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
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Source?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    exit() {
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
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Exit?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    VolumeDown() {
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
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/VolumeDown?api-version=2022-05-31`,
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    VolumeUp() {
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
        `https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/VolumeUp?api-version=2022-05-31`,
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