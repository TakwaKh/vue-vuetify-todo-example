<template>
<nav>
    <v-app-bar
        app
        color="white"
        flat
    >
    <v-app-bar-nav-icon @click="drawer =!drawer"></v-app-bar-nav-icon>
    <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light">todo</span>
            <span>ninja</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>

        <v-menu offset-y open-on-hover transition="slide-y-transition">
            <template v-slot:activator="{ on, attrs }">
                <v-btn depressed v-bind="attrs" v-on="on" class="mx-5">
                Menu
                </v-btn>
            </template>
            <v-list>
                <v-list-item v-for="link in links" :key="link.index" router :to="link.route" color="indigo">
                <v-list-item-title>{{link.text}}</v-list-item-title>
                </v-list-item>
            </v-list>
        </v-menu>


        <v-btn depressed>
            <span>Sign Out</span>
            <v-icon right>mdi-login-variant</v-icon>
        </v-btn>
    </v-app-bar>
     <v-navigation-drawer app
      v-model="drawer">
      <v-row>
          <v-col col="12" class="text-center my-4">
              <v-avatar size="100">
                <img
                  src="https://cdn.vuetifyjs.com/images/john.jpg"
                  alt="you"
                >
              </v-avatar>
              <div class="mt-3 text-subtitle">  The Net Ninja</div>
          </v-col>
      </v-row>
      <v-row class="text-center">
          <v-col>
              <Popup/>
          </v-col>
      </v-row>
      
      <v-list nav dense >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4">
          <v-list-item v-for="link in links" :key="link.index" router :to="link.route">
            <v-list-item-title>
                <v-icon left small>{{link.icon}}</v-icon>
                <span>{{link.text}}</span>
                </v-list-item-title>
          </v-list-item>


        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
</nav>
</template>

<script>
// @ is an alias to /src

import Popup from './Popup';

export default {
  name: 'Navbar',
  components: {
      Popup
  },
  data() {
      return {
        drawer: false,
        group: false,
        links: [
         { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/' },
         { icon: 'mdi-folder', text: 'My Projects', route: '/Projects' },
         { icon: 'mdi-account', text: 'Team', route: '/Team' },
       ]
      }
  }
}
</script>
