<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      dark
      app
    >
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed dark hide-on-scroll app>
      <v-app-bar-nav-icon class="hidden-sm-and-up" @click.stop="drawer = !drawer" />

      <v-toolbar-title v-text="title" />
      <v-icon>{{logoPath}}</v-icon>
      <v-spacer />
      <v-toolbar-items v-for="(item,i) in items" :key="i" class="hidden-xs-only">
        <v-btn flat :to="item.to">
          <v-icon>{{item.icon}}</v-icon>
          {{item.title}}
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <v-footer :absolute="!fixed" app>
      <v-col class="text-center" cols="12">&copy; {{ new Date().getFullYear() }} {{title}}</v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "News",
          to: "/"
        },
        {
          icon: "mdi-chart-bubble",
          title: "About",
          to: "/about"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "News24x7",
      logoPath: "/news-logo.png"
    };
  }
};
</script>
