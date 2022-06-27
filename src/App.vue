<template>
  <v-app>
    <v-container>
      <v-app-bar
          absolute
          color="teal lighten-3"
          dark
      >
        <v-row>
          <v-col cols="11">
            <h4>Task Manager</h4>
          </v-col>
          <v-col cols="1">
            <v-btn class="float-right"
                   @click="dialog = true"
                   color="primary"
                   dark
            >Create
            </v-btn>
          </v-col>
        </v-row>
      </v-app-bar>
    </v-container>
    <v-container>
      <template>
        <v-row justify="center">
          <v-dialog
              v-model="dialog"
              persistent
              max-width="600px"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                  color="primary"
                  dark
                  v-bind="attrs"
                  v-on="on"
              >
                Create
              </v-btn>
            </template>
            <v-card>
              <v-card-title>
                <span class="text-h5">Create task</span>
              </v-card-title>
              <v-card-text>
                <v-container>
                  <v-form ref="form">
                    <v-row>
                      <v-col cols="12" sm="12" md="12" lg="12" xl="12">
                        <v-text-field
                            v-model="tasktitle"
                            label="Title"
                            required
                            outlined
                            color="primary"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="12" md="12" lg="12" xl="12">
                        <v-textarea
                            v-model="taskdescription"
                            label="Description"
                            outlined
                            color="primary"
                        ></v-textarea>
                      </v-col>
                    </v-row>
                  </v-form>
                </v-container>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    color="blue"
                    text
                    @click="cancel"
                >
                  Close
                </v-btn>
                <v-btn
                    color="blue"
                    text
                    @click="save"
                >
                  Save
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </v-row>
      </template>

      <template>
        <v-row>
          <v-col cols="4" v-for="(task) in tasks" :key="task.id">
            <v-card>
              <v-card-title>
                <span class="text-h5">{{ task.title }}</span>
              </v-card-title>
              <v-card-text>
                {{ task.description }}
              </v-card-text>
            </v-card>
          </v-col>

        </v-row>
      </template>

    </v-container>
  </v-app>

</template>

<script>


export default {
  name: 'App',

  components: {},

  data: () => ({
    firstname: '',
    lastname: '',
    dialog: false,
    tasks: [],
    tasktitle: '',
    taskdescription: '',
    taskid: 1,
  }),
  methods: {
    clear: function () {
      this.tasktitle = '';
      this.taskdescription = '';
    },
    save: function () {
      this.tasks.push({
        id: this.taskid,
        title: this.tasktitle,
        description: this.taskdescription
      });
      this.taskid = this.taskid + 1
      this.dialog = false;
      this.clear()
    },
    cancel: function () {
      this.clear()
      this.dialog = false;
    }
  }
};
</script>
