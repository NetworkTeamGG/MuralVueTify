<template>
  <div class="navbar">
    <v-app-bar app color="purple white-1" flat min-width="840px">
      <v-container class="py-0 fill-height">
        <v-icon aria-hidden="false" color="white" size="50"> mdi-home </v-icon>
        <v-spacer> </v-spacer>
        <v-responsive max-width="260"> </v-responsive>
      </v-container>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
</style>