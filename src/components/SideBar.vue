<script setup>
import VNavigationDrawer from 'vuetify/lib/components/VNavigationDrawer'
</script>

<template>
    <VNavigationDrawer>
            <v-list-item>
                <v-list-item-content>
                    <v-list-item-title class="title">
                        Baris Buba
                    </v-list-item-title>
                    <v-list-item-subtitle>
                        testing unit
                    </v-list-item-subtitle>
                </v-list-item-content>
            </v-list-item>

        <v-divider></v-divider>

            <v-expansion-panels>
                <v-expansion-panel>
                    <v-expansion-panel-header>
                        Text
                    </v-expansion-panel-header>
                    <v-expansion-panel-content>
                        <draggable v-model="listText" ghost-class="ghost" @end="onEndButton" group="test">
                            <transition-group type="transition" name="flip-list">
                                <div class="sortable" :id="element.id" v-for="element in listText" :key="element.id">
                                <strong>{{ element.name }}</strong>
                                <span>{{ element.id }}</span>
                                <v-form>
                                    <v-container>
                                        <v-row>
                                            <v-col cols="6" sm="3" md="2">
                                                <v-text-field label="name" class="inputField"></v-text-field>
                                            </v-col>
                                        <v-col cols="6" sm="3" md="2">
                                            <v-text-field label="age" class="inputField"></v-text-field>
                                        </v-col>
                                        </v-row>
                                     </v-container>
                                </v-form>
                                </div>
                            </transition-group>
                        </draggable>
                    </v-expansion-panel-content>
                </v-expansion-panel>
            </v-expansion-panels>

            <v-expansion-panels>
                <v-expansion-panel>
                    <v-expansion-panel-header>
                        Buttons
                    </v-expansion-panel-header>
                    <v-expansion-panel-content>
                        <draggable v-model="listButton" ghost-class="ghost" @end="onEndText" group="test" :clone="clone">
                            <transition-group type="transition" name="flip-list">
                                <v-btn class="sortable" :id="element.id" v-for="element in listButton" :key="element.id">
                                <strong>{{ element.name }}</strong>
                                <span>{{ element.id }}</span>
                                </v-btn>
                            </transition-group>
                        </draggable>
                    </v-expansion-panel-content>
                </v-expansion-panel>
            </v-expansion-panels>

    </VNavigationDrawer>    
</template>

<script>
import draggable from 'vuedraggable'

let idGlobal = 8;

export default {
  name: 'SideBarMenu',
  components: {
      draggable
  },
  props:{
    msg: String
  },
  data(){
      return{
          listText: [
                {name: 'Value1 ', id: "ID " + 0},

          ],

            listButton:[
                {name: 'button1', id: "ID " + 8},
            ],

          oldIndex: '',
          newIndex: ''
      }
  },
  methods: {
    clone({ name }) {
        console.log("this is happening");
      return { name, id: idGlobal++ };
      
    },

      onEndButton: function (event) {
        event.listButton.add(event.newIndex, event.listButton.splice(event.oldIndex, 1)[0])
      },

      onEndText: function (event) {
          event.listText.add(event.newIndex, event.listText.splice(event.oldIndex, 1)[0])
      }

      
  }
}
</script>

<style scoped>
h1 {
  margin: 40px 0 0;
}

strong{
  display: inline-block;
}

.sortable{
  width: 100%;
  background: white;
  padding: 1em;
  cursor: move;
  margin-bottom: 2px;
}

.ghost {
      border-left: 6px solid rgb(0, 183, 255);
      box-shadow: 10px 10px 5px -1px rgba(0,0,0,0.14);
      opacity: 0.7;

}

</style>
