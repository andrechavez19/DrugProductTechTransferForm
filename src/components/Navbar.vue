<template>
    <nav>
    <v-app-bar app >
      <v-app-bar-nav-icon @click = "drawer = !drawer"></v-app-bar-nav-icon>
      <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src= "../assets/Aji_BioPharma.jpg"
          transition="scale-transition"
          width="200"
        />
      <v-toolbar-title >Drug Product Manufacturing Tech Transfer</v-toolbar-title>
  
      <v-spacer></v-spacer>
  
      <v-btn depressed @click = "sign_out">
          <span>Sign Out</span>
          <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
          absolute
          temporary
          app
          v-model="drawer"
        >
          <v-list
            dense
            nav
            class="py-0"
          >
            <v-list-item two-line class='px-0'>
              <v-list-item-avatar>
                <img src="../assets/red_sphere.svg">
              </v-list-item-avatar>
  
              <v-list-item-content>
                <v-list-item-title>Client Name</v-list-item-title>
                <v-list-item-subtitle>Product Name</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
  
            <v-divider></v-divider>
  
            <v-list-item
              v-for="item in items"
              :key="item.title"
              link
              @click = "viewform(item.title)"
            >
              <v-list-item-icon>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-icon>
  
              <v-list-item-content>
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-navigation-drawer>
    </nav>
  
</template>

<script>
import { mapGetters } from 'vuex'
export default {
computed: mapGetters(['getAuthenticationData']),

    data: () => ({
        drawer: false,
        items: [
        //{ title: 'Process Overview', icon: 'mdi-view-dashboard' },
        { title: 'Home', icon: 'mdi-home-outline' },
        { title: 'Program Information', icon: 'mdi-folder-outline' },
        { title: 'Manufacturing', icon: 'mdi-hexagon-multiple-outline' },
        { title: 'Logistics', icon: 'mdi-truck-outline' },
        { title: 'Health and Safety', icon: 'mdi-hospital-box-outline' },
        { title: 'Quality Control Testing', icon: 'mdi-flask' },
        { title: 'Document Uploads', icon: 'mdi-file-document-box-plus-outline' }
      ],
  }),
  methods:{
      viewform(form){
          this.drawer = !this.drawer
          this.$emit('change_form', form);
      },
      sign_out(){
        this.getAuthenticationData.authenticated = false;
      }

  }

}
</script>
