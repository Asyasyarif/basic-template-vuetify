<template>
  <v-app id="inspire">
    <v-navigation-drawer  v-model="sidebarMenu" app :permanent="sidebarMenu">
        <v-list>
            <v-list-item>
                <v-list-item-content>
                    <v-list-item-title>
                        Projekt-wlan.com
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-divider></v-divider>
          <v-list>
              <v-list-item v-for="item in items" :key="item.title" link :to="item.href">
                  <v-list-item-icon>
                      <v-icon >{{ item.icon }}</v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                      <v-list-item-title>{{ item.title }}</v-list-item-title>
                  </v-list-item-content>
              </v-list-item>
        </v-list>
    </v-navigation-drawer>

    <v-app-bar app flat>
      <v-app-bar-nav-icon @click="sidebarMenu = !sidebarMenu"></v-app-bar-nav-icon>
      <v-toolbar-title>Welcome</v-toolbar-title>
      <v-spacer></v-spacer>
        <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <v-menu bottom left >
          <template v-slot:activator="{ on, attrs }">
            <v-btn  icon v-bind="attrs" v-on="on" >
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>

          <v-list>
            <v-list-item link
              v-for="(item, i) in items" :key="i">
              <v-list-item-title >{{ item.title }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>

    <v-main>
      <v-container fluid>

      </v-container>
    </v-main>
    <v-footer app>
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} — <strong>Projekt-wlan.com</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
 
  },

    computed: {
    mini() {
        return (this.$vuetify.breakpoint.smAndDown) || this.toggleMini
    },
    buttonText() {
        return !this.$vuetify.theme.dark ? 'Go Dark' : 'Go Light'
    }
  },

  data: () => ({ 
     sidebarMenu: true,
    drawer: null ,
      items: [
        { title:"Home", href:"/", icon:"mdi-home-outline" },
        { title:"Detections", href:"/detections", icon:"mdi-shield-account" },
        { title:"Components", href:"/comp", icon:"mdi-palette-swatch" },
        { title:"Customers", href:"/customers", icon:"mdi-account-search-outline" },
        { title:"Orders", href:"/orders", icon:"mdi-bus-clock" },
        { title:"Settings", href:"/settings", icon:"mdi-settings-outline" },
      ],
    }),
};
</script>


<style scoped>

</style>