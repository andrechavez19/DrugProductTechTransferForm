<template>
  <v-app>
      <v-app-bar
      app
      color="secondary"
      dark>

        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src= "./assets/Aji_BioPharma.jpg"
          transition="scale-transition"
          width="200"
        />
        <v-app-bar-title text = "#EE1C26">Client Tech Transfer Form</v-app-bar-title>
        <v-spacer>    </v-spacer>
        <v-spacer>    </v-spacer>
        <a class="d-flex align-right">Sign Out</a>
    </v-app-bar>
    <br>
    <br>
    <v-content>
        <v-container>
            <h3>Client Products</h3>
            <h5>Please select a product you have manufactured with us.</h5>
            <br>
            <v-row v-for = "product in products" :key="product.index">
                <v-col>
                <v-btn v-on:click="getProductForm()">{{product}}</v-btn>
                </v-col>
            </v-row>
        </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {

    data(){
			return {

            products: ["Product 1", "Product 2"]

            }
  
  },
  methods:{
      getProductForm() {
          this.$router.push('/ClientPortalForm')


      }


  }

}
</script>

<style>

</style>