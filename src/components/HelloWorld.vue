<template>
  <v-row align="center" justify="center">
    <v-sheet align="center" justify="center" class="pa-12" width="900" height="820" tile>
      <v-img src="/noonoo.gif" class="mb-12" aspect-ratio="1" max-width="200" max-height="200"></v-img>
      <v-form ref="form">
        <v-combobox v-model="select" :items="items" label="Koji je objektiv funkcije?"></v-combobox>
        <div>
<<<<<<< HEAD
          <v-data-table :headers="headers" :items="varijable">
            
=======
          <v-data-table hide-default-footer :headers="headers" :items="varijable">
>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
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
<<<<<<< HEAD

            <template v-slot:item.iron="props">
              <v-edit-dialog :return-value.sync="props.item.iron" large persistent @save="save" @cancel="cancel" @open="open" @close="close">
                <div>{{ props.item.iron }}</div>
=======
            <template v-slot:item.x1="props">
              <v-edit-dialog
                :return-value.sync="props.item.x1"
                large
                persistent
                @save="save"
                @cancel="cancel"
                @open="open"
                @close="close"
              >
                <div>{{ props.item.x1 }}</div>
>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
                <template v-slot:input>
                  <div class="mt-4 title">Update Iron</div>
                </template>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.x1"
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
        <br />
        <v-btn color="success" class="mr-4" @click="solve">RIJEŠI</v-btn>
      </v-form>
    </v-sheet>
  </v-row>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      select: ["max"],
      brvarijabli: "",
      brogranicenja: "",
      selected: ["max"],
      items: ["max", "min"],
      snack: false,
      snackColor: "",
      snackText: "",
      max25chars: v => v.length <= 25 || "Input too long!",
      pagination: {},
      headers: [
        {
          text: "",
          value: "name"
        },
        { text: "x1", value: "x1" },
        { text: "x2", value: "x2" },
        { text: "x3", value: "x3" },
        { text: "x4", value: "x4" },
        { text: "x5", value: "x5" },
        { text: ">=", value: "min" },
        { text: "<=", value: "max" },
        { text: "b", value: "b" }
      ],
<<<<<<< HEAD
      
=======

>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
      varijable: [
        {
          name: "Z = ",
          x1: 0.12,
          x2: 0.057,
          x3: 0.049,
          x4: 0.044,
          x5: 0.036,
          //min: true,
          //max: false,
          //b: 4
        },
        {
          name: "(1)",
          x1: 1,
          x2: 1,
          x3: 1,
          x4: 1,
          x5: 1,
          min: true,
          max: false,
          b: 1178887.68
        },
        {
          name: "(2)",
          x1: 0.85,
          x2: -0.15,
          x3: -0.15,
          x4: -0.15,
          x5: -0.15,
          min: true,
          max: false,
          b: 0
        },
        {
          name: "(3)",
          x1: -0.3,
          x2: 0.7,
          x3: -0.3,
          x4: -0.3,
          x5: -0.3,
          min: true,
          max: false,
          b: 0
        },
        {
          name: "(4)",
          x1: -0.4,
          x2: -0.4,
          x3: 0.6,
          x4: -0.4,
          x5: -0.4,
          min: true,
          max: false,
          b: 0
        },
        {
          name: "(5)",
          x1: -0.15,
          x2: -0.15,
          x3: -0.15,
          x4: 0.85,
          x5: -0.15,
          min: true,
          max: false,
          b: 0
        },
        {
          name: "(6)",
          x1: -0.15,
          x2: -0.15,
          x3: -0.15,
          x4: -0.15,
          x5: 0.85,
          min: true,
          max: false,
<<<<<<< HEAD
          b: 0
        },
=======
          b: 4
        }
>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
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
          optimize: "cilj",
          opType: "max",
          constraints: {
<<<<<<< HEAD
            x6: {max: 1176667.68},
            x7: {max: 0},
            x8: {min: 0},
            x9: {max: 0},
            x10: {min: 0},
            x11: {min: 0}
=======
            x6: { max: 1176667.68 },
            x7: { max: 0 },
            x8: { min: 0 },
            x9: { max: 0 },
            x10: { min: 0 },
            x11: { min: 0 }
>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
          },
          variables: {
            x1: {
              cilj: 0.12,
              x6: 1,
              x7: 0.85,
              x8: -0.3,
              x9: -0.4,
              x10: -0.15,
              x11: -0.15
            },
            x2: {
              cilj: 0.057,
              x6: 1,
              x7: -0.15,
              x8: 0.7,
              x9: -0.4,
              x10: -0.15,
              x11: -0.15
<<<<<<< HEAD
            },
            x3: {
              cilj: 0.049,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: 0.6,
              x10: -0.15,
              x11: -0.15
            },
            x4: {
              cilj: 0.044,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: -0.4,
              x10: 0.85,
              x11: -0.15
            },
            x5: {
              cilj: 0.036,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: -0.4,
              x10: -0.15,
              x11: 0.85
            },
=======
            },
            x3: {
              cilj: 0.049,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: 0.6,
              x10: -0.15,
              x11: -0.15
            },
            x4: {
              cilj: 0.044,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: -0.4,
              x10: 0.85,
              x11: -0.15
            },
            x5: {
              cilj: 0.036,
              x6: 1,
              x7: -0.15,
              x8: -0.3,
              x9: -0.4,
              x10: -0.15,
              x11: 0.85
            }
>>>>>>> e7bae9d755a85d6336e4ed596c5499b879a436cd
          }
        };
      results = solver.Solve(model);
      console.log(results);
    }
  }
};
</script>
