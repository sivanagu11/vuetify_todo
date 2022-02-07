<template>
  <div class="Home">
    <v-container mt-16>
      <div class="radius">
        <v-row justify="center" class="my-16">
          <v-card
            cols="4"
            class="pt-5 px-10"
            height="700px"
            width="600px"
            overflow="hidden"
            display="fixed"
          >
           <v-menu
          :close-on-content-click="false"
          transition="scale-transition"
          offset-y
         
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              v-bind="attrs"
              v-on="on"
              class="indigo darken-4 white--text"
               absolute
                center
                :style="{left: '95%', transform:'translateX(-95%)'}"

            > calender</v-btn>
          </template>
          <v-date-picker
            v-model="date"
            no-title
          ></v-date-picker>
        </v-menu>
            <h2 class="px-4">Today</h2>
              
            <v-list flat>
              <div v-for="task in tasks" :key="task.id">
                <v-list-item v-if="task.date == getTodaydate()" @click="doneTask(task.id)">
                  <template v-slot:default>
                    <v-list-item-action>
                      <v-checkbox :input="task.done"></v-checkbox>
                    </v-list-item-action>

                    <v-list-item-content>
                      <v-list-item-title
                        :class="{ 'text-decoration-line-through': task.done }"
                      >
                        {{ task.title }}
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-list-item-action>
                      <v-btn @click.stop="deleteTask(task.id)" icon>
                        <v-icon color="black">mdi-delete</v-icon>
                      </v-btn>
                    </v-list-item-action>
                  </template>
                </v-list-item>
              </div>
            </v-list>

            <h2 class="px-4">Tommorrow</h2>
            <v-list flat>
              <div v-for="task in tasks" :key="task.id">
                <v-list-item v-if="task.date == getTommorrowdate()" @click="doneTask(task.id)">
                  <template v-slot:default>
                    <v-list-item-action>
                      <v-checkbox
                        :input="task.done"
                        color="primary"
                      ></v-checkbox>
                    </v-list-item-action>

                    <v-list-item-content>
                      <v-list-item-title
                        :class="{ 'text-decoration-line-through': task.done }"
                      >
                        {{ task.title }}
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-btn @click.stop="deleteTask(task.id)" icon>
                      <v-icon color="black">mdi-delete</v-icon>
                    </v-btn>
                  </template>
                </v-list-item>
              </div>
            </v-list>
             <h2 class="px-4">Upcoming</h2>
            <v-list flat>
              <div v-for="task in tasks" :key="task.id">
                <v-list-item v-if="task.date == getUpcomingDate()" @click="doneTask(task.id)">
                  <template v-slot:default>
                    <v-list-item-action>
                      <v-checkbox
                        :input="task.done"
                        color="primary"
                      ></v-checkbox>
                    </v-list-item-action>

                    <v-list-item-content>
                      <v-list-item-title
                        :class="{ 'text-decoration-line-through': task.done }"
                      >
                        {{ task.title }}
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-btn @click.stop="deleteTask(task.id)" icon>
                      <v-icon color="black">mdi-delete</v-icon>
                    </v-btn>
                  </template>
                </v-list-item>
              </div>
            </v-list>
           
            <v-text-field
              v-model="newTaskTitle"
              @click:append-outer="addTask"
              @keyup.enter="addTask"
              class="pa-3"
              outlined
              label="add new task"
              append-outer-icon="mdi-plus-circle "
              color="teal"
            >
             </v-text-field>
         
            

          </v-card>
        </v-row>
      </div>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: "",
      date: "",
      tasks: [
        
      ],
      newTask: null
    };
  },
  methods: {
    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
    },

    
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        date: this.date,
        done: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
      localStorage.setItem('tasks',JSON.stringify(newTask));
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },   
    getTodaydate(){
      console.log(this.date)
      let d = new Date();
      return d.toISOString().split("T")[0];
    },
    getTommorrowdate() {
      let d = new Date();
      d.setDate(d.getDate() + 1);
     return d.toISOString().split("T")[0];
    },
    getUpcomingDate(){
          let d = new Date();
      d.setDate(d.getDate() + 7);
     return d.toISOString().split("T")[0];
     

    },
  },
};
</script>







