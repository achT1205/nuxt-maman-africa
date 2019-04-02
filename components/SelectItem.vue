<template>
  <v-select
    v-model="selected"
    :hint="`${selected.label}, ${selected.id}`"
    :items="items"
    item-text="label"
    item-value="id"
    :label="label"
    persistent-hint
    return-object
    single-line
    mandatory
    browser-autocomplete
    :append-icon="icon && icon.length > 0? icon :''"
    menu-props="auto"
    hide-details
    :change="handelSelectChange(selected)"
  ></v-select>
</template>


<script lang="ts">
import { Component, Vue, Prop } from "nuxt-property-decorator";

@Component({
  props: {
    handelSelectChange: {
      required: true
    },
    items: {
      required: true,
      type: Array
    },
    selectedItem: {
      required: true,
      type: Object
    },
    label: {
      required: true,
      type: String
    },
    icon: {
      type: String
    }
  },
  components: {}
})
export default class SelectItem extends Vue {
  public selectedItem: any;
  public selected: any = {};

  mounted() {
    this.selected = this.selectedItem;
  }
}
</script>
