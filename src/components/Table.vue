<template>
    <div class="px-5">
        <v-data-table
            :headers="masterHeaders"
            :items="masterData"
            show-expand
            :expanded.sync="expandedRows"
            :single-expand="true"
            @click:row="fetchSubDetails"
        >
            <template v-slot:top>
                <v-toolbar flat>
                    <v-toolbar-title class="text-center">Master-Details Table Data</v-toolbar-title>
                </v-toolbar>
            </template>

            <template v-slot:expanded-item="{ item }">
                <td :colspan="masterHeaders.length + 1">
                    <div class="pa-2 my-4">
                        <h4> More details for {{ item.name }}:</h4>
                        <v-data-table
                            :headers="detailsHeaders"
                            :items="detailsData"
                            :hide-default-footer="true"
                            item-key="id"
                            dense
                            :single-select="true"
                            :expanded.sync="expanded"
                        >
                        </v-data-table>
                    </div>
                </td>
            </template>
        </v-data-table>
    </div>
</template>

<script>
  export default {
    props: ['masterHeaders', 'masterData'],
    data() {
      return {
        expanded: [],
        search: "",
        detailsHeaders: [],
        detailsData: []
      };
    },
    methods: {
        fetchSubDetails(item) {
            // fetch('https://jsonplaceholder.typicode.com/todos/1')
            // .then(response => response.json())
            // .then(json => console.log(json))
            this.detailsHeaders = [
                { text: "Salary", value: "salary" },
                { text: "Occupation", value: "occupation" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" },
                { text: "Hobby", value: "hobby" }
            ];

            this.detailsData = [
                {
                    id: 1,
                    salary: `$ ${23000 * item.id}`,
                    occupation: 'Software Engineer',
                    hobby: "Diving",
                },
                {
                    id: 2,
                    salary: `$ ${213000 * item.id}`,
                    occupation: 'Rigging',
                    hobby: "Sleeping",
                },
                {
                    id: 3,
                    salary: `$ ${320000 * item.id}`,
                    occupation: 'Politician',
                    hobby: "Clubbing",
                }
            ]
            this.expanded.push(item);
        }
    },
    computed: {
        expandedRows: {
            set(value) {
                this.expanded = value;
                if (value.length > 0) {
                    this.fetchSubDetails(value[0]);
                }
            },
        },
    }
  };
</script>
