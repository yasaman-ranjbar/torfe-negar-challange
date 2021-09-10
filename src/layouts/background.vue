<template>
  <v-app>
    <v-main class="grey lighten-2">
      <v-row>
        <v-col class="teal darken-1 py-16" cols="12"></v-col>
            <v-container>
                <router-view></router-view>
            </v-container>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
export default {};
</script>

<style scoped>
</style>