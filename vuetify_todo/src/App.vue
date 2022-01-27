<template>
<v-row>
  <v-col>
  <v-app id="inspair">
    <v-navigation-drawer color="#FFFFFF" v-model="drawer" app>
      <v-list-item>
        <v-list-item-content class="#000000--text">
          <v-list-item-title class="text-h6">
            Todo Task 
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" 
        :key="item.title" 
        :to="item.to"
         link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app color="#1A237E" >
      <v-app-bar-nav-icon class="white--text" @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title class="white--text">Todos</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-icon  class="pr-10" color="white" >mdi-refresh</v-icon>

     
    </v-app-bar>
    <main>
     <router-view></router-view>
    </main>
  </v-app>
  </v-col>
</v-row>
</template>
<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: "Todo", icon: "mdi-format-list-checks", to: "/" },
      { title: "About", icon: "mdi-help-box", to: "/about" },
    ],
  }),
};
</script>
<style>
#inspair{
  background-image: url('../src/assets/photo-1533035336122-4327d347d2fe.jpg');

  margin: 0;
  padding: 0;
}
</style>







