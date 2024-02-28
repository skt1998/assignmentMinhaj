<template>
  <v-container class="pa-8">
    <v-row justify="center">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >

      <v-card>
        <v-card-title>
          <span class="text-h5">Create Task</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="12"
                md="12"
              >
                <v-text-field
                  label="Enter Task Name*"
                  required
                  v-model="name"
                  outlined
                  hide-details
                ></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-textarea
      v-model="description"
      label="Task Description"
      counter
      maxlength="120"
      hide-details
      full-width
  outlined
    ></v-textarea>
              </v-col>

            </v-row>
          </v-container>

        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>


    <v-dialog
      v-model="editDialog"
      persistent
      max-width="600px"
    >

      <v-card>
        <v-card-title>
          <span class="text-h5">Edit Task</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="12"
                md="12"
              >
                <v-text-field
                  label="Enter Task Name*"
                  required
                  v-model="name"
                  outlined
                  hide-details
                ></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-textarea
      v-model="description"
      label="Task Description"
      counter
      maxlength="120"
      hide-details
      full-width
  outlined
    ></v-textarea>
              </v-col>

            </v-row>
          </v-container>

        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="editDialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="editDialog = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>

   <v-card width="100%" class="pa-4 mb-4 d-flex  flex-row justify-space-between">


    <h5 class="text-h5 font-weight-medium">Tasks</h5>

    <div>
      <v-btn class="mr-4 rounded-xl">delete</v-btn> <v-btn @click="dialog = true" class="rounded-xl grey">Create</v-btn>


    </div>

   </v-card>
   <v-data-table
      :headers="headers"
      :items="desserts"
      item-key="name"
      class="elevation-1"
      :search="search"
      show-select 
      v-model="selected"
      :custom-filter="filterOnlyCapsText"
    >
      <template v-slot:top>
        <v-text-field
          v-model="search"
          label="Search (UPPER CASE ONLY)"
          class="mx-4"
        ></v-text-field>
      </template>

      <template v-slot:[`item.actions`]="{ item }">
          <div class="d-flex flex-row">
            <v-btn icon @click="edit(item)" ><v-icon>mdi-pencil</v-icon></v-btn>
          </div>
        </template>
 
    </v-data-table>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      selected: [],
      search: '',
      name: "",
      description: "",
      dialog: false,
      editDialog: false,
        calories: '',
        desserts: [
          {
            name: 'Frozen Yogurt',
            description: "this is description of task",
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: 1,
          },
          {
            name: 'Ice cream sandwich',
            description: "this is description of task",

            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: 1,
          },
          {
            name: 'Eclair',
            description: "this is description of task",

            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: 7,
          },
          {
            name: 'Cupcake',
            description: "this is description of task",

            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            iron: 8,
          },
          {
            name: 'Gingerbread',
            description: "this is description of task",

            fat: 16.0,
            carbs: 49,
            protein: 3.9,
            iron: 16,
          },
          {
            name: 'Jelly bean',
            description: "this is description of task",

            fat: 0.0,
            carbs: 94,
            protein: 0.0,
            iron: 0,
          },
          {
            name: 'Lollipop',
            description: "this is description of task",

            fat: 0.2,
            carbs: 98,
            protein: 0,
            iron: 2,
          },
          {
            name: 'Honeycomb',
            description: "this is description of task",

            fat: 3.2,
            carbs: 87,
            protein: 6.5,
            iron: 45,
          },
          {
            name: 'Donut',
            description: "this is description of task",

            fat: 25.0,
            carbs: 51,
            protein: 4.9,
            iron: 22,
          },
     
        ],
    }),
    methods: {
      edit(item){
        this.editDialog = true;
        this.name = item.name;
        this.description = item.description;
      },
    },
    computed: {
      headers () {
        return [
          {
            text: 'Task Name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          {
            text: 'Description',
            value: 'description',
   
          },
          { text: 'Created On', value: 'fat' },
          { text: 'Edit', value: 'actions' },
        ]
      },
    },
  }
</script>
