<template>
  <div class="Home">
    <v-container mt-16>
      <div class="radius">
        <v-row justify="center" class="my-16">
          <v-card
            cols="4"
            class="pt-5 px-10"
            height="600px"
            width="500px"
            overflow="hidden"
            display="fixed"
          >
            <h2 class="px-4">Today</h2>

            <v-list flat>
              <div v-for="task in tasks" :key="task.id">
                <v-list-item @click="doneTask(task.id)">
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
              <div v-for="item in items" :key="item.id">
                <v-list-item @click="doneItem(item.id)">
                  <template v-slot:default>
                    <v-list-item-action>
                      <v-checkbox
                        :input="item.done"
                        color="primary"
                      ></v-checkbox>
                    </v-list-item-action>

                    <v-list-item-content>
                      <v-list-item-title
                        :class="{ 'text-decoration-line-through': item.done }"
                      >
                        {{ item.title }}
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-btn @click.stop="deleteItem(item.id)" icon>
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
              hide-details
              clearable
            ></v-text-field>
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
      tasks: [
        {
          id: 1,
          title: "Going to office",
          done: false,
        },
        {
          id: 2,
          title: "learning new concepts",
          done: false,
        },
        {
          id: 3,
          title: "practice more ",
          done: false,
        },
      ],
      newTask: null,
      items: [
        {
          id: 1,
          title: "learn vuetify",
          done: false,
        },
        {
          id: 2,
          title: "practice vuetify",
          done: false,
        },
        {
          id: 3,
          title: "learn grid",
          done: false,
        },
      ],
    };
  },
  methods: {
    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
    },

    doneItem(id) {
      let item = this.items.filter((item) => item.id === id)[0];
      item.done = !item.done;
    },
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
    },
    deleteTask(id){
      this.tasks=this.tasks.filter(task => task.id !== id)
    },
    deleteItem(id){
   this.items=this.items.filter(item => item.id !== id)
    }
    
  },
};
</script>







