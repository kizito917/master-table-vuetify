<template>
    <v-app>
      <v-app-bar
        app
        color="primary"
        dark
      >
        <div class="d-flex align-center">
          <h4>Master Detail Table</h4>
        </div>
      </v-app-bar>

      <v-main>
        <Table :masterHeaders="masterHeaders" :masterData="masterData" />
      </v-main>
    </v-app>
</template>

<script>
import Table from './components/Table.vue';

export default {
  name: 'App',

  components: {
    Table,
  },

  data: () => ({
    masterHeaders: [
        { text: "Name", value: "name" },
        { text: "Age", value: "age" },
        { text: "Gender", value: "gender" },
        { text: "Description", value: "description" }
    ],
    masterData: [
        {
            id: 1,
            name: "John",
            age: 30,
            gender: "Male",
            description: "John is a software developer."
        },
        {
            id: 2,
            name: "Jane",
            age: 25,
            gender: "Female",
            description: "Jane is a graphic designer."
        },
        {
            id: 3,
            name: "Bob",
            age: 40,
            gender: "Male",
            description: "Bob is a project manager."
        },
        {
            id: 4,
            name: "Daniel",
            age: 10,
            gender: "Male",
            description: "Daniel is a UI designer."
        },
        {
            id: 5,
            name: "Angela",
            age: 12,
            gender: "Female",
            description: "Angela is a Talent acquisition manager."
        }
    ],
  }),
};
</script>
