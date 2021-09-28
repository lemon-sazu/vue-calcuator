<template>
  <v-container>
    <v-col cols="12">
      <div
        class="pa-4 pt-2 pb-1 mb-1 rounded-t-xl"
        style="background: #deeefd; color: #1e85f2"
      >
        <v-card-text class="text-h4 font-weight-normal text-right pr-0">
          {{ results() }}
        </v-card-text>
        <div class="text-h5 font-weight-light text-right mb-4">{{ tnum }}</div>
      </div>
      <div
        class="pa-4 pb-8 rounded-b-xl"
        style="background: #deeefd; color: #1e85f2"
      >
        <v-row>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#31c2ff"
              style="font-size: 20px"
              @click="tnum = ''"
              >C</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#31c2ff"
              style="font-size: 20px"
              @click="type_num((number = '%'))"
              >%</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              dark
              fab
              @click="type_num((number = '/'))"
              class="rounded-pill"
              color="#31c2ff"
              style="font-size: 20px"
              >÷</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              dark
              fab
              class="rounded-pill"
              color="#1a7aff"
              style="font-size: 20px"
              @click="slice_last_charec()"
              >CE</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              @click="type_num((number = 7))"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              >7</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 8))"
              >8</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 9))"
              >9</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              @click="type_num((number = '*'))"
              color="#1a7aff"
              style="font-size: 20px"
              >×</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 4))"
              >4</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 5))"
              >5</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 6))"
              >6</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              @click="type_num((number = '-'))"
              elevation="2"
              fab
              dark
              color="#1a7aff"
              style="font-size: 20px"
              >-</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 1))"
              >1</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 2))"
              >2</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 3))"
              >3</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              @click="type_num((number = '+'))"
              elevation="2"
              fab
              dark
              color="#1a7aff"
              style="font-size: 20px"
              >+</v-btn
            >
          </v-col>
          <v-col cols="6" align="center">
            <v-btn
              elevation="2"
              block
              dark
              large
              class="rounded-pill mt-2"
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = 0))"
              >0</v-btn
            >
          </v-col>
          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#e91e63"
              style="font-size: 20px"
              @click="type_num((number = '.'))"
              >.</v-btn
            >
          </v-col>

          <v-col cols="3" align="center">
            <v-btn
              elevation="2"
              fab
              dark
              color="#1a7aff"
              style="font-size: 20px"
              @click="submit_results()"
              >=</v-btn
            >
          </v-col>
        </v-row>
      </div>
    </v-col>
  </v-container>
</template>

<script>
export default {
  name: "Calculator",
  watch: {},
  data() {
    return {
      answer: 0,

      clear_one: false,

      tnum: "",
      n_split: "",
    };
  },
  methods: {
    results() {
      return this.answer;
    },
    removeduplicate(string) {
      return string
        .split("")
        .filter(function (item, pos = ".", self) {
          console.log(self.indexOf(item));
          return self.indexOf(item) == pos;
        })
        .join("");
    },
    type_num() {
      const num = String(this.number);
      this.tnum += num;
    },

    submit_results() {
      const tnum = this.tnum;
      console.log(this.removeduplicate(tnum));
      if (tnum.includes("+")) {
        this.n_split = tnum.split("+");
        console.log(Number(this.n_split[0]) + Number(this.n_split[1]));
        this.answer = Number(this.n_split[0]) + Number(this.n_split[1]);
        this.tnum = this.answer;
      }
      if (tnum.includes("-")) {
        this.n_split = tnum.split("-");
        this.answer = Number(this.n_split[0]) - Number(this.n_split[1]);
        this.tnum = this.answer;
      }
      if (tnum.includes("*")) {
        this.n_split = tnum.split("*");
        this.answer = Number(this.n_split[0]) * Number(this.n_split[1]);
        this.tnum = this.answer;
      }
      if (tnum.includes("/")) {
        this.n_split = tnum.split("/");
        this.answer = Number(this.n_split[0]) / Number(this.n_split[1]);
        this.tnum = this.answer;
      }
      if (tnum.includes("%")) {
        this.n_split = tnum.split("%");
        this.answer = (Number(this.n_split[0]) * Number(this.n_split[1])) / 100;
        this.tnum = this.answer;
      }
    },
    slice_last_charec() {
      const tnum = String(this.tnum);
      this.tnum = tnum.slice(0, -1);
    },
  },
};
</script>