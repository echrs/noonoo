<template>
  <v-row align="center" justify="center">
    <v-sheet width="700" height="700" tile>
      <v-img src="/noonoo.gif" aspect-ratio="1" max-width="200" max-height="200"></v-img>
      <v-form ref="form">
        <v-text-field v-model="brvarijabli" label="Broj varijabli?"></v-text-field>
        <v-text-field v-model="brogranicenja" label="Broj ograničenja?"></v-text-field>
        <v-select v-if="brogranicenja" :items="items" label="Koji je objektiv funkcije?"></v-select>
        <div>
          <v-data-table :headers="headers" :items="varijable">
            <template v-slot:item.name="props">
              <v-edit-dialog :return-value.sync="props.item.name" @save="save" @cancel="cancel" @open="open" @close="close">
                {{ props.item.name }}
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.name"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>
            <template v-slot:item.iron="props">
              <v-edit-dialog
                :return-value.sync="props.item.iron"
                large
                persistent
                @save="save"
                @cancel="cancel"
                @open="open"
                @close="close"
              >
                <div>{{ props.item.iron }}</div>
                <template v-slot:input>
                  <div class="mt-4 title">Update Iron</div>
                </template>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.iron"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                    autofocus
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>
          </v-data-table>

          <v-snackbar v-model="snack" :timeout="3000" :color="snackColor">
            {{ snackText }}
            <v-btn text @click="snack = false">Close</v-btn>
          </v-snackbar>
        </div>
        <v-btn color="success" class="mr-4" @click="solve">Solve</v-btn>
        <v-btn color="error" class="mr-4" @click="reset">Reset Form</v-btn>
      </v-form>
    </v-sheet>
  </v-row>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      brvarijabli: "",
      brogranicenja: "",
      items: ["max", "min"],
      snack: false,
      snackColor: "",
      snackText: "",
      max25chars: v => v.length <= 25 || "Input too long!",
      pagination: {},
      headers: [
        {
          text: "",
          sortable: false,
          value: "name"
        },
        { text: "x1", value: "x1" },
        { text: "x2", value: "x2" },
        { text: "x3", value: "x3" },
        { text: "x4", value: "x4" },
        { text: "x5", value: "x5" },
        { text: ">=", value: "min" },
        { text: "<=", value: "max" },
        { text: "b", value: "b" },

      ],
      varijable: [
        {
          name: "Z = ",
<<<<<<< HEAD
          x1: 159,
          x2: 6.0,
          x3: 24,
          x4: 4.0,
          x5: "1%"
=======
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
>>>>>>> a78476b116171ef411bae13bd1b65294edf69ef4
        },
        {
          name: "(1)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
        {
          name: "(2)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
        {
          name: "(3)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
        {
          name: "(4)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
        {
          name: "(5)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
        {
          name: "(6)",
          x1: 2,
          x2: 11,
          x3: 2,
          x4: 5,
          x5: 4,
          min: true,
          max: false,
          b: 4
        },
      ]
    };
  },
  methods: {
    save() {
      this.snack = true;
      this.snackColor = "success";
      this.snackText = "Data saved";
    },
    cancel() {
      this.snack = true;
      this.snackColor = "error";
      this.snackText = "Canceled";
    },
    open() {
      this.snack = true;
      this.snackColor = "info";
      this.snackText = "Dialog opened";
    },
    close() {
      console.log("Dialog closed");
    },
    reset() {
      this.$refs.form.reset();
    },
    solve() {
      var solver = require("javascript-lp-solver"),
        results,
        model = {
          optimize: "capacity",
          opType: "max",
          constraints: {
            plane: { max: 44 },
            person: { max: 512 },
            cost: { max: 300000 }
          },
          variables: {
            x1: {
              capacity: 20000,
              plane: 1,
              person: 8,
              cost: 5000
            },
            x2: {
              capacity: 30000,
              plane: 1,
              person: 16,
              cost: 9000
            },
            x3: {
              capacity: 30000,
              plane: 1,
              person: 16,
              cost: 9000
            },
            x4: {
              capacity: 30000,
              plane: 1,
              person: 16,
              cost: 9000
            },
            x5: {
              capacity: 30000,
              plane: 1,
              person: 16,
              cost: 9000
            },

          }
        };

      results = solver.Solve(model);
      console.log(results);
    }
  }
};
</script>
