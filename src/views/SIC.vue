<template>
  <div class="">
    <Home v-if="isOK" />
    <Fail v-if="!isOK" />
  </div>
</template>
    
    
    <script>
import Fail from "./Fail.vue";
import Home from "./Home.vue";

export default {
  name: "PostCheck",
  created() {
    this.getPosts();
  },

  mounted() {
    // document.onclick = ()=> {
    //     this.idleSecondsCouter = 0;
    // };
    // document.onmousemove = ()=> {
    //     this.idleSecondsCouter = 0;
    // };
    document.onmousepress = () => {
      this.idleSecondsCouter = 0;
    };
    this.idleSecondsTimer = window.setInterval(this.CheckIdleTime, 1000);
  },
  data() {
    return {
      IDLE_TIMEOUT: 300,
      idleSecondsTimer: 0,
      idleSecondsCouter: 0,
      isOK: true,
    };
  },
  methods: {
    CheckIdleTime() {
      this.idleSecondsCouter++;
      //var oPanel = this.IDLE_TIMEOUT - this.idleSecondsCouter;
      if (this.idleSecondsCouter >= this.IDLE_TIMEOUT) {
        window.clearInterval(this.idleSecondsTimer);
        alert("Time expired!");
        this.$router.push("/timeout");
      }
    },
    getPosts() {
      var myHeaders = new Headers();
      var requestOptions = {
        method: "GET",
        headers: myHeaders,
        redirect: "follow",
      };
      var uid = new URLSearchParams(window.location.search).get("U");
      var timestamp = new URLSearchParams(window.location.search).get("TS");
      var sac = new URLSearchParams(window.location.search).get("SAC");
      fetch(
        `https://testsic43s1cmac.azurewebsites.net/api/cmaccal?U=${uid}&TF=00&TS=${timestamp}&SAC=${sac}`,
        requestOptions
      )
        .then((response) => response.json())
        .then((result) => {
          console.log(result.result);
          if (result.result == "OK") {
            //this.$router.push("/home");
            this.isOK = true;
          } else if (result.result == "Reused") {
            //this.$router.push("/about");
            this.isOK = false;
          } else if (result.result == "Fail") {
            //this.$router.push("/about");
            this.isOK = false;
          }
        })

        .catch((error) => {
          console.log(error);
          this.errorMsg = "Error data";
        });
    },
  },
  components: { Home, Fail },
};
</script>
     
    
  