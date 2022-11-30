<template>
  <v-app-bar app color="##90a4ae" flat>

    <div class="logo">
			<!--<img :src="logoURL" alt="Vue" /> -->
			<img src="../assets/sic.png" contain width="30" alt="Vue" /> 
		</div>
    <v-toolbar-title class="ml-4">
      <span class="blue--text">Silicon </span><strong>Craft Technology</strong>
    </v-toolbar-title>

    <v-spacer></v-spacer>

    <!-- <v-btn icon dark class="">
      <v-icon x-small color="#878A94">fas fa-temperature-low</v-icon>
    </v-btn>

    <v-btn icon dark class="">
      <v-icon x-small color="#878A94">fas fa-tv</v-icon>
    </v-btn> -->
  </v-app-bar>
</template>

<script>
export default {};
</script>

<style>
.v-toolbar__title {
  font-size: 1rem !important;
}
</style>