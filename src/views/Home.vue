<template>
  <v-app>
    <Navbar />
    <v-container fluid>
      <v-row>
        <v-col cols="12">
          
          <v-toolbar flat color="transparent" class="mt-1">
            <v-toolbar-title class="text-h6">SMART TV</v-toolbar-title>
            <v-spacer></v-spacer>
            <!-- <v-btn rounded color="black" dark class="px-8">POWER</v-btn> -->

            <v-btn icon dark class="red" @click="onOfftv">
              <v-icon x-small color="white" style='font-size: 25px'>fas fa-power-off </v-icon>
            </v-btn>


            <!-- <v-btn rounded color="black" dark class="px-8">
              <v-icon color="white" left>fas fa-power-off</v-icon>
              on-off
            </v-btn> -->
          </v-toolbar>

          <Tv />

          <v-toolbar flat color="transparent" class="mt-5">
            <v-toolbar-title class="text-h6">AIR CONDITIONER</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon dark class="red"  @click="onOffair">
              <v-icon x-small color="white" style='font-size: 25px'>fas fa-power-off </v-icon>
            </v-btn>
            <!-- <v-btn rounded color="green" dark class="px-8">See All</v-btn> -->
          </v-toolbar>
          <Air />
    
        
            <Fan />

            <Level />
         
       
          

        </v-col>
      </v-row>
    </v-container>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from "../components/Navbar";
import Tv from "../components/Tv.vue";
import Air from "../components/Air.vue";
import Level from "../components/Level.vue";



export default {
  name: "Home",
  data: () => ({
    toggle_exclusive: 1,
    TV : false,
    Air : false
  }),
  components: {
    Navbar,
    Tv,
    Air,
    Level
   
},
  methods: {
    onOffair() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg%3D&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");

      var raw = JSON.stringify({
        request: this.Air = !this.Air ,
      });
      
      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };

      fetch(
        "https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/PowerAir?api-version=2022-05-31",
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
    onOfftv() {
      var myHeaders = new Headers();
      myHeaders.append(
        "Authorization",
        "SharedAccessSignature sr=dce8fbd5-7966-4d6b-a18a-e9624253f140&sig=KH6cG9EHRO7sbyWqL0GEReH9pk3l4I5B7rl3njQNLRg%3D&skn=test&se=1689828641992"
      );
      myHeaders.append("Content-Type", "application/json");
      
      var raw = JSON.stringify({
        request: this.TV = !this.TV ,
      });

      var requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: raw,
        redirect: "follow",
      };

      fetch(
        "https://sic-esp32-test.azureiotcentral.com/api/devices/sic-esp32/commands/Power?api-version=2022-05-31",
        requestOptions
      )
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
  },
};
</script>
<style >
.marginLeft {
  margin-left: -90px;
}
.mtop {
  margin-top: 100px;
}
.mbottom {
  margin-bottom: 100px;
}
.v-card.borderme {
  border: 2px solid green !important;
}
.v-card.borderout {
  border: 1px solid #d5f0db !important;
}
.v-btn:not(.v-btn--round).v-size--default.add {
  min-width: 0px !important;
}
.theme--light.v-sheet--outlined.mobile {
  border: 2px solid black !important;
}
@media only screen and (max-width: 600px) {
  h2.title1 {
    font-size: 15px;
  }
  h2.title2 {
    font-size: 15px;
  }
  .top {
    margin-top: 20px;
  }
}
@media only screen and (min-width: 600px) {
  .top {
    margin-top: 70px;
  }
}
@media only screen and (min-width: 768px) {
  .top {
    margin-top: 120px;
  }
}
</style>
