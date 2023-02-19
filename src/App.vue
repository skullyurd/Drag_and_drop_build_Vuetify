<script setup>
  import SideBar from "./components/SideBar.vue";
  import DragDropZone from "./components/DragDropZone.vue";
</script>

<template>
  <v-app>

    <v-navigation-drawer app v-model="drawer">
      <SideBar/>
    </v-navigation-drawer>

    
    <v-content>
      <DragDropZone/>
    </v-content>
  </v-app>
</template>


<style lang="scss">

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: grey;
  color: black;
}

.dropZone .sortable-drag {
  opacity:  0;

}

.flip-list-move {
  transition: transform 0.5s;
}

</style>