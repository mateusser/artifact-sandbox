<template>
  <div id="app">
    <v-app light>
      <v-navigation-drawer
        fixed
        :mini-variant="miniVariant"
        clipped
        app
      >
        <v-list>
          <v-list-tile 
            router
            :to="item.to"
            :key="i"
            v-for="(item, i) in items"
            exact
          >
            <v-list-tile-action>
              <v-icon v-html="item.icon"></v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>
      <v-toolbar fixed app clipped-left>
        <v-toolbar-side-icon
          @click.native.stop="miniVariant = !miniVariant"
        ></v-toolbar-side-icon>
        <v-toolbar-title v-text="title"></v-toolbar-title>
        <v-spacer></v-spacer>
      </v-toolbar>
      <v-content>
        <v-container fluid fill-height>
          <v-slide-y-transition mode="out-in">
            <router-view></router-view>
          </v-slide-y-transition>
        </v-container>
      </v-content>
      <v-footer fixed app>
        <v-spacer></v-spacer>
        <span class="footer">Mateus Seehagen Rodrigues &copy; 2018</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
  export default {
    name: 'artifact-sandbox',
    data: () => ({
      items: [
        { icon: 'apps', title: 'Welcome', to: '/' }
      ],
      miniVariant: true,
      title: 'Artifact Cards'
    })
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons');
/* Global CSS */

.footer {
  margin-right: 10px;
}
</style>
