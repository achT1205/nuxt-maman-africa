<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app>
      <v-list>
        <v-list-tile v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"/>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :clipped-left="clipped" fixed app>
      <v-toolbar-side-icon @click="drawer = !drawer"/>
      <v-btn v-if="drawer" icon @click.stop="miniVariant = !miniVariant">
        <v-icon>{{ `chevron_${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"/>
      <v-flex class="ml-5 mr-5">
        <v-text-field
          class="search-field"
          v-model="search"
          label="Search"
          :append-icon="search.length > 0 ? 'close':'search'"
        ></v-text-field>
      </v-flex>
      <v-btn icon>
        <v-icon>notifications</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>favorite</v-icon>
      </v-btn>
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>more_vert</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt/>
      </v-container>
    </v-content>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-tile>
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "nuxt-property-decorator";

@Component({})
export default class extends Vue {
  clipped: boolean = false;
  drawer: boolean = false;
  fixed: boolean = true;
  items: any[] = [
    {
      icon: "view_list",
      title: "Welcome",
      to: "/"
    },
    {
      icon: "add_to_photos",
      title: "Add",
      to: "/announcements/add"
    },
    {
      icon: "shopping_basket",
      title: "Shop",
      to: "/announcements/shop"
    }
  ];
  miniVariant: boolean = true;
  right: boolean = true;
  rightDrawer: boolean = false;
  title: string = "Maman africa";
  search: string = "";
}
</script>
<style>
.container {
  background: none;
}
</style>
