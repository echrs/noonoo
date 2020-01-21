<template>
  <v-row align="center" justify="center" class="grey lighten-3">
    <v-sheet elevation="5" align="center" justify="center" class="pa-12 mt-12 mb-12" width="900" height="880" normal>
      <v-img src="/noonoo.gif" class="mb-12" aspect-ratio="1" max-width="200" max-height="200"></v-img>
      <v-form ref="form">
        <v-combobox v-model="select" :items="items"  label="Koji je objektiv funkcije?"></v-combobox>
        <div>
          <v-data-table hide-default-footer disable-sort :headers="headers" :items="item">
            <template v-slot:item.name="props">
              <v-edit-dialog :return-value.sync="props.item.name">
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
            </template>            <template v-slot:item.x1="props">
              <v-edit-dialog :return-value.sync="props.item.x1" large persistent>
                <div>{{ props.item.x1 }}</div>
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
            </template>            <template v-slot:item.x2="props">
              <v-edit-dialog :return-value.sync="props.item.x2" large persistent>
                <div>{{ props.item.x2 }}</div>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.x2"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                    autofocus
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>            <template v-slot:item.x3="props">
              <v-edit-dialog :return-value.sync="props.item.x3" large persistent>
                <div>{{ props.item.x3 }}</div>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.x3"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                    autofocus
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>            <template v-slot:item.x4="props">
              <v-edit-dialog :return-value.sync="props.item.x4" large persistent>
                <div>{{ props.item.x4 }}</div>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.x4"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                    autofocus
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>            <template v-slot:item.x5="props">
              <v-edit-dialog :return-value.sync="props.item.x5" large persistent>
                <div>{{ props.item.x5 }}</div>
                <template v-slot:input>
                  <v-text-field
                    v-model="props.item.x5"
                    :rules="[max25chars]"
                    label="Edit"
                    single-line
                    counter
                    autofocus
                  ></v-text-field>
                </template>
              </v-edit-dialog>
            </template>            <template v-slot:item.minmax="props">
              <v-edit-dialog :return-value.sync="props.item.minmax" large persistent>
                <div>{{ props.item.minmax }}</div>
                <template v-slot:input>
                  <v-combobox v-model="props.item.minmax" :items="items"></v-combobox>
                </template>
              </v-edit-dialog>
            </template>
          </v-data-table>
        </div>
        <br />
       
      </v-form>
      <!-- van forme -->
      <div class="my-2 mb-12">
        <v-btn depressed large color="primary" @click="solve">RIJEŠI</v-btn>
      </div>
    </v-sheet>
  </v-row>
</template><script>
export default {
  name: "HelloWorld",
  data() {
    return {
      select: ["max"],
      items: ["max", "min"],
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
        { text: ">=/<=", value: "minmax" },
        { text: "b", value: "b" }
      ],      item: [
        {
          name: "Z = ",
          x1: 0.12,
          x2: 0.057,
          x3: 0.049,
          x4: 0.044,
          x5: 0.036
        },
        {
          name: "(1)",
          x1: 1,
          x2: 1,
          x3: 1,
          x4: 1,
          x5: 1,
          minmax: "max",
          b: 1178887.68
        },
        {
          name: "(2)",
          x1: 0.85,
          x2: -0.15,
          x3: -0.15,
          x4: -0.15,
          x5: -0.15,
          minmax: "max",
          b: 0
        },
        {
          name: "(3)",
          x1: -0.3,
          x2: 0.7,
          x3: -0.3,
          x4: -0.3,
          x5: -0.3,
          minmax: "min",
          b: 0
        },
        {
          name: "(4)",
          x1: -0.4,
          x2: -0.4,
          x3: 0.6,
          x4: -0.4,
          x5: -0.4,
          minmax: "max",
          b: 0
        },
        {
          name: "(5)",
          x1: -0.15,
          x2: -0.15,
          x3: -0.15,
          x4: 0.85,
          x5: -0.15,
          minmax: "min",
          b: 0
        },
        {
          name: "(6)",
          x1: -0.15,
          x2: -0.15,
          x3: -0.15,
          x4: -0.15,
          x5: 0.85,
          minmax: "min",
          b: 0
        }
      ]
    };
  },
  methods: {
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
            x6: { [this.item[1].minmax]: this.item[1].b },
            x7: { [this.item[2].minmax]: this.item[2].b },
            x8: { [this.item[3].minmax]: this.item[3].b },
            x9: { [this.item[4].minmax]: this.item[4].b },
            x10: { [this.item[5].minmax]: this.item[5].b },
            x11: { [this.item[6].minmax]: this.item[6].b }
          },
          variables: {
            x1: {
              cilj: this.item[0].x1,
              x6: this.item[1].x1,
              x7: this.item[2].x1,
              x8: this.item[3].x1,
              x9: this.item[4].x1,
              x10: this.item[5].x1,
              x11: this.item[6].x1
            },
            x2: {
              cilj: this.item[0].x2,
              x6: this.item[1].x2,
              x7: this.item[2].x2,
              x8: this.item[3].x2,
              x9: this.item[4].x2,
              x10: this.item[5].x2,
              x11: this.item[6].x2
            },
            x3: {
              cilj: this.item[0].x3,
              x6: this.item[1].x3,
              x7: this.item[2].x3,
              x8: this.item[3].x3,
              x9: this.item[4].x3,
              x10: this.item[5].x3,
              x11: this.item[6].x3
            },
            x4: {
              cilj: this.item[0].x4,
              x6: this.item[1].x4,
              x7: this.item[2].x4,
              x8: this.item[3].x4,
              x9: this.item[4].x4,
              x10: this.item[5].x4,
              x11: this.item[6].x4
            },
            x5: {
              cilj: this.item[0].x5,
              x6: this.item[1].x5,
              x7: this.item[2].x5,
              x8: this.item[3].x5,
              x9: this.item[4].x5,
              x10: this.item[5].x5,
              x11: this.item[6].x5
            }
          }
        };
      results = solver.Solve(model);
      console.log(results);
    }
  }
};
</script>

<style lang="scss">
.gumb {
  color: white;
}
.background-color {
  color: black
}
</style>