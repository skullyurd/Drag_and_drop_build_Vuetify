<template>
    <div>
        <v-container>
        <div class="dropZone">
            <h1>drop zone</h1>

            <draggable v-model="listText" ghost-class="ghost" @end="onEnd" group="test">
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
                              
                              <v-col>
                                <!--delete button-->
                              </v-col>

                            </v-row>
                          </v-container>
                          
                        </v-form>
                    </div>
                </transition-group>
            </draggable>

            <draggable v-model="listButton" ghost-class="ghost" @end="onEnd" group="test">
                <transition-group type="transition" name="flip-list">
                    <v-btn class="sortable" :id="element.id" v-for="element in listButton" :key="element.id">
                        <strong>{{ element.name }}</strong>
                        <span> {{  element.id }}</span>
                      </v-btn>
                </transition-group>
            </draggable>

            <p><strong>Previous Index: </strong> {{ oldIndex }}</p>
            <p><strong>New Index: </strong> {{ newIndex }}</p>
        </div>
    </v-container>
    </div>
    
</template>
  
  <script>
  import draggable from 'vuedraggable'
  
  export default {
    name: 'dragDropZone',
    components: {
        draggable
    },
    props:{
      msg: String
    },
    data(){
        return{
          listText: [
                {name: 'Value1 ', id: 0},
                {name: 'Value2 ', id: 1},
                {name: 'Value3 ', id: 2},
                {name: 'Value4 ', id: 3},
                {name: 'Value5 ', id: 4},
                {name: 'Value5 ', id: 5},
                {name: 'Value6 ', id: 6},
            ],

            listButton:[
                {name: 'button1', id: 7},
            ],

            oldIndex: '',
            newIndex: ''
        }
    },
    methods: {
        onEnd: function (event) {
            console.log(event)
            this.oldIndex = event.oldIndex
            this.newIndex = event.newIndex
        },
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

  .inputField {
    width: 100px;
    margin: 0 10px;
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
  