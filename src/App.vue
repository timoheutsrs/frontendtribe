<template>
  <v-app>
    <v-form>
      <v-container>
        <v-row>
          <v-col cols="3"></v-col>
          <v-col cols="6">
            <v-card
                cols="6"
                elevation="12"
                class="pa-3"
            >

              <v-text-field v-model="firstname"
                label="First name"></v-text-field>
              <v-text-field
                  label="Last name"
              v-model="lastname"></v-text-field>
              <v-btn
                  color="primary"
                  elevation="2"
                  v-on:click="clear"
              >
                Clear
              </v-btn>

              <v-card class="mt-3 pa-3">
                {{firstname}} {{lastname}}
              </v-card>

            </v-card>

          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
  },

  data: () => ({
    firstname:'',
    lastname: '',

    //
  }),
  methods: {
    clear: function () {
      this.firstname = '';
      this.lastname='';
    }
  }
};
</script>
