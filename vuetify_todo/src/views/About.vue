<template>
  <v-container mt-16>
    <div>
      <v-row justify="center" class="my-12">
        <v-card class="px-16" height="400px" width="400px">
          <v-card-title>
            <h2>About Me</h2>
          </v-card-title>
          <form>
            <v-text-field
              v-model="Name"
              class="input"
              outlined
              label=" Full Name"
            >
            </v-text-field>
            <v-text-field
              v-model="Email"
              class="input"
              outlined
              label="Email Address"
            >
            </v-text-field>
            <v-text-field
              v-model="Github"
              class="input"
              outlined
              label="Github link"
            >
            </v-text-field>
            <v-btn color="success" class="mx-2" @click="submit"> submit </v-btn>
            <v-btn color="success" class="mx-8" @click="clear">clear</v-btn>
          </form>
        </v-card>
      </v-row>
    </div>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      Name: "",
      Email: "",
      Github: "",
    };
  },
  methods: {
    submit() {
      console.log(this.Name, this.Email, this.Github);
    },
    clear() {
      (this.Name = ""), (this.Email = ""), (this.Github = "");
    },
  },
};
</script>



