<template>
  <div class="container">
    <div>
      <Input @myResult="myResult" />
    </div>
    <div>
      <Output :result="result"/>
    </div>
  </div>
</template>

<script>
import Input from "./components/Input.vue";
import Output from "./components/Output.vue";

export default {
  data() {
    return {
        result :null,
    };
  },
  components: { Input, Output },

  methods: {
    myResult(res) {
        this.result = res ; 
        console.log(this.result);
    },
  },
};
</script>

<style scoped>
.container {
  width: 100%;
  height: 100vh;
  display: flex;
  margin: auto;
  justify-content: space-around;
  background-color: rgb(193, 252, 232);
}
</style>
