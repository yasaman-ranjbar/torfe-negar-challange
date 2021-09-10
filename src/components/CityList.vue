<template>
  <v-card class="mx-auto" flat>
    <v-toolbar color="#f0f2f5">
      <v-toolbar-title>City List</v-toolbar-title>
    </v-toolbar>

    <v-list three-line>
      <v-list-item-group v-model="selectedItem" color="#00a884">
        <template v-for="(item, index) in items">
          <v-subheader
            v-if="item.header"
            :key="item.header"
            v-text="item.header"
          ></v-subheader>

          <v-divider
            v-else-if="item.divider"
            :key="index"
            :inset="item.inset"
          ></v-divider>

          <v-list-item exact v-else :key="item.title">
            <v-list-item-avatar>
              <v-img :src="item.avatar"></v-img>
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title @click="fireCity(item.title)" v-html="item.title">
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  props: {
      items: [],
  },
  data: () => ({
    selectedItem: 1,
    
  }),

  methods: {
    fireCity(e) {
        // const nameCity = this.items.find( x => x.title == e)
        // console.log(nameCity);
      this.$emit('selectCity' , e)
    },
  },
};
</script>

<style>
</style>