<template>
  <v-container>
    <v-card :height="taille">
      <v-col>
        <v-card-title class="green white--text">
          <span class="text-h5">Menu</span>

          <v-spacer></v-spacer>

          <v-menu  
        bottom
        auto
        left
        offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn dark icon v-bind="attrs" v-on="on">
                <v-icon>mdi-dots-vertical</v-icon>
              </v-btn>
            </template>
            <v-list nav dense>
              <v-menu open-on-hover top offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-list-item v-bind="attrs" v-on="on">
                    <v-list-item-title>
                    <v-list-item-icon>
                      <v-icon> mdi-home </v-icon>
                    </v-list-item-icon>
                      {{ Menus[0].Menu }}
                    </v-list-item-title>
                  </v-list-item>
                </template>
                <v-list>
                  <v-list-item v-for="(item, index) in items" :key="index">
                    {{ item.title }}
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-list>
            <v-list nav dense>
              <v-menu open-on-hover bottom offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-list-item v-bind="attrs" v-on="on">
                    <v-list-item-icon>
                      <v-icon> mdi-home </v-icon>
                    </v-list-item-icon>
                    <v-list-item-title>
                      {{ Menus[1].Menu }}
                    </v-list-item-title>
                  </v-list-item>
                </template>
                <v-list>
                  <v-list-item v-for="(item, index) in items" :key="index">
                    {{ item.title }}
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-list>
          </v-menu>
        </v-card-title>
      </v-col>
      <!-- <v-app-bar dark>
        <v-toolbar-title>
          {{ Dashbord }}
        </v-toolbar-title>
        <v-spacer></v-spacer>

        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>
         </v-app-bar> -->

      <!-- <v-list nav dense>     
           <v-menu
        open-on-hover
        bottom
        offset-y
        >
       <template v-slot:activator="{on, attrs}">
         <v-list-item v-bind="attrs"
                v-on="on"
          >
          <v-list-item-icon>
            <v-icon>
              mdi-home
            </v-icon>
          </v-list-item-icon>
          <v-list-item-title>
            {{Menus[1].Menu}}
          </v-list-item-title>
         </v-list-item>
       </template>
       <v-list>
         <v-list-item
         v-for="(item,index) in items"
         :key="index">
         {{item.title}}
         </v-list-item>      
       </v-list>
        </v-menu> 
      </v-list> -->
      <tab />
    </v-card>
  </v-container>
</template>

<script>
import tab from "@/components/tab.vue";
export default {
  name: "NavBar",
  components: { tab },
  data: () => ({
    logo: "https://via.placeholder.com/120",
    Dashbord: "Menu",
    taille: 850,
    Menus: [{ Menu: "Menu 1" }, { Menu: "Menu 2" }, { Menu: "Menu 3" }],
    drawer: false,
    group: null,
    items: [{ title: "1" }, { title: "2" }, { title: "3" }, { title: "4" }],
    methods: {
      getmenu() {
        console.log(this.Menus[0].Menu);
      },
    },
  }),
};
</script>

<style scoped>
img {
  border-radius: 50%;
  border: 5px #333 solid;
  margin-bottom: 10px;
}
</style>
