<template>
  <v-card flat>
    <v-container v-for="type in types" :key="type" fluid grid-list-md grey lighten-4>
      <v-layout row wrap>
        <v-spacer></v-spacer>
        <v-flex v-for="card in cards" :key="card" xs12 sm6 md3>
          <v-card>
            <v-img :src="`https://picsum.photos/200/300?image=${getImage()}`" height="200px">
              <span class="headline white--text pl-3 pt-3" v-text="card.title"></span>
            </v-img>
            <v-card-text
              class="">"Turns out semicolon-less style ases are type i"</v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn icon>
                <v-icon>favorite</v-icon>
              </v-btn>
              <v-btn icon>
                <v-icon>share</v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </v-card>
</template>

<script lang="ts">
import { Component, Vue } from "nuxt-property-decorator";
import Card from "~/components/Card.vue";

@Component({
  components: {
    Card
  }
})
export default class extends Vue {
  types: any[] = ["Places to Be", "Places to See"];
  cards: any[] = ["Good", "Best", "Finest", "Top"];
  socials: any[] = [
    {
      icon: "fab fa-facebook",
      color: "indigo"
    },
    {
      icon: "fab fa-linkedin",
      color: "cyan darken-1"
    },
    {
      icon: "fab fa-instagram",
      color: "red lighten-3"
    }
  ];
  getImage() {
    const min = 550;
    const max = 560;

    return Math.floor(Math.random() * (max - min + 1)) + min;
  }
}
</script>


<style scoped>
.header {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.cards {
  display: flex;
  flex-wrap: wrap;
}
</style>
