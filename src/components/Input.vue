<template>
  <div class="input_box">
    <div><h4>Input</h4></div>
    <div>
      <label for="search"></label>
      <input type="text" id="search" v-model="search" class="input_search" @input="search_message" />
    </div>
    <div>
      <div class="options"><h4>Options</h4></div>
      <div class="box_checkbox">
        <div>
          <input type="checkbox" id="Split" v-model="split" @click="split = !split" />
          <label for="Split">Split by spice</label>
        </div>
        <div>
          <input type="checkbox" id="Case" v-model="case" />
          <label for="Case">Case sensitive</label>
        </div>
      </div>
      <div class="options"><h4>search target search</h4></div>
      <textarea class="textarea" v-model="message"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      message: "",
      split: true,
      case: false,
      arraySplit: [],
      arrayCase: [],
      result: [],
      searchArray: [],
    };
  },
  methods: {
    search_message() {
      this.search.split(" ").filter((item) => {
        this.searchArray.push(item);
      });
      let array = this.message.split(" ");
      let Case = array.filter((item) => {
        return item.charAt(0).toUpperCase() === item;
      });
      if (this.split === true) {
        if (this.searchArray.length) {
          array.filter((item) => {
            if (item === this.searchArray[this.searchArray.length - 1]) {
              this.result.push(item);
            }
          });
        } else {
          array.filter((item) => {
            if (item === this.search) {
              this.result.push(item);
            }
          });
        }
      } else {
        this.result = Case.filter((item) => {
          return item === this.search;
        });
      }
      if (!this.search.length) {
        this.result = [];
      }
      console.log(Case);
      let sum = this.result;
      this.$emit("myResult", sum);
    },
  },
};
</script>

<style scoped>
.input_box {
  padding: 20px;
  margin-top: 100px;
  min-width: 45vh;
  min-height: 70%;
  background-color: white;
}
.input_search {
  margin-top: 20px;
  width: 450px;
  height: 30px;
  border: 1px solid rgb(169, 253, 183);
}
.box_checkbox {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
}
.options {
  margin-top: 20px;
}
.textarea {
  width: 450px;
  height: 500px;
}
</style>
