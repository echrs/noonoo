<template>
  <v-container>
    <v-row class="justify-center">
       <v-col cols="2"></v-col> 
      <v-col cols="8">
        <v-sheet
          elevation="2"
          align="center"
          justify="center"
          class="pa-12 mt-12 mb-12"
          normal
        >
          <v-img src="/noonoo.gif" class="mb-12" aspect-ratio="1" max-width="200" max-height="200"></v-img>
          <v-form ref="form">
            <v-combobox
              v-model="select"
              :items="items"
              outlined
              dense
              label="Što radimo s funkcijom cilja?"
              class="mb-5"
            ></v-combobox>
              <v-card class="mb-6" outlined>
              <v-data-table hide-default-footer disable-sort :headers="headers" :items="item">
                <!-- x1 -->
                <template v-slot:item.x1="props">
                  <v-edit-dialog :return-value.sync="props.item.x1" large persistent>
                    <div>{{ props.item.x1 }}</div>
                    <template v-slot:input>
                      <v-text-field v-model="props.item.x1" type="number" single-line></v-text-field>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- x2 -->
                <template v-slot:item.x2="props">
                  <v-edit-dialog :return-value.sync="props.item.x2" large persistent>
                    <div>{{ props.item.x2 }}</div>
                    <template v-slot:input>
                      <v-text-field v-model="props.item.x2" type="number" single-line></v-text-field>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- x3 -->
                <template v-slot:item.x3="props">
                  <v-edit-dialog :return-value.sync="props.item.x3" large persistent>
                    <div>{{ props.item.x3 }}</div>
                    <template v-slot:input>
                      <v-text-field v-model="props.item.x3" type="number" single-line></v-text-field>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- x4 -->
                <template v-slot:item.x4="props">
                  <v-edit-dialog :return-value.sync="props.item.x4" large persistent>
                    <div>{{ props.item.x4 }}</div>
                    <template v-slot:input>
                      <v-text-field v-model="props.item.x4" type="number" single-line></v-text-field>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- x5 -->
                <template v-slot:item.x5="props">
                  <v-edit-dialog :return-value.sync="props.item.x5" large persistent>
                    <div>{{ props.item.x5 }}</div>
                    <template v-slot:input>
                      <v-text-field v-model="props.item.x5" type="number" single-line></v-text-field>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- MIN / MAX -->
                <template v-slot:item.minmax="props">
                  <v-edit-dialog :return-value.sync="props.item.minmax" large persistent>
                    <div>{{ props.item.minmax }}</div>
                    <template v-slot:input>
                      <v-combobox v-model="props.item.minmax" :items="items"></v-combobox>
                    </template>
                  </v-edit-dialog>
                </template>

                <!-- RHS -->
                <template v-slot:item.b="props">
                  <v-edit-dialog :return-value.sync="props.item.b" large persistent>
                    <div>{{ props.item.b }}</div>
                    <template v-slot:input>
                      <v-combobox v-model="props.item.b" type="number" single-line></v-combobox>
                    </template>
                  </v-edit-dialog>
                </template>
              </v-data-table>
              </v-card>
          </v-form>

          <v-row class="d-flex justify-content-between justify-center">
            <v-col cols="6">
              <div v-if="result == null || result == 0">
                <v-alert :value="alert" type="error">Nešto nije u redu.</v-alert>
              </div>
                <!-- dismissible  -->
              <div v-else>
                <v-alert :value="alert" type="success">Dobiveno je optimalno rješenje.</v-alert>
              </div>
            </v-col>
            <v-col cols="6">
              <v-btn depressed large class="mt-2" color="white--text light-blue darken-1" :value="alert" @click="solve">RIJEŠI</v-btn>
            </v-col>
          </v-row>
         <div class="my-2 mb-12">
            <v-card outlined class="mt-6">
              <v-card-title ><h6 class="idipavidi">Rezultat modela</h6></v-card-title>
              <v-divider></v-divider>
              <v-list dense rounded>
                <v-list-item>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>x1:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ x1 }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>x2:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ x2 }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>x3:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ x3 }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>x4:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ x4 }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>x5:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ x5 }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-content class="align-end"> 
                    <v-list-item-title>Z:</v-list-item-title>
                    <v-list-item-subtitle class="align-end">{{ result }}</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card>
          <!-- </v-row> -->
        </div>
        </v-sheet>
      </v-col>
       <v-col cols="2" > </v-col> 
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "NooNoo",
  data() {
    return {
      alert: false,
      feasible: false,
      result: "",
      bounded: "",
      x1: "",
      x2: "",
      x3: "",
      x4: "",
      x5: "",
      select: "max",
      items: ["max", "min"],
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
        { text: ">= | <=", value: "minmax" },
        { text: "RHS", value: "b" }
      ],
      //default vrijednosti
      item: [
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
  watch: {
    result: function (result) {
    console.log("Watch aktiviran");
      this.alert=true;
      }
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
          opType: this.select,
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
      results = JSON.stringify(results);
      var object = JSON.parse(results);
      console.log(results);
      this.feasible = object.feasible;
      this.result = object.result;
      this.bounded = object.bounded;
      this.x1 = Math.round(object.x1);
      this.x2 = Math.round(object.x2);
      this.x3 = Math.round(object.x3);
      this.x4 = Math.round(object.x4);
      this.x5 = Math.round(object.x5);
      return object;
    }
  }
};
</script>

<style lang="scss">
.idipavidi {
  text-align: center;
  color: #0d0d0d;
  font-size: 18px;
  font-weight: normal;
}
</style>
