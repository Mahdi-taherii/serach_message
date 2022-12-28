<template>
  <div class="output">
    <div><h4>Output</h4></div>
    <div><h4>search words</h4></div>
    <div class="box_item">
      <div v-for="(item, index) in result" :key="index" >
        <div class="item">{{ item }}</div>
      </div>
    </div>
    <div><h4>Matched word count</h4></div>
    <div >{{ result.length }}</div>
  </div>
</template>

<script>

export default {
  props: {
    result: {
      default: [""],
    },
  },
  data() {
    return {
      arrayMessage: this.result,
    };
  },
};
</script>

<style scoped>
.output {
  margin-top: 100px;
  min-width: 500px;
  min-height: 70%;
  background-color: white;
}
.box_item{
    display:flex;
    flex-wrap: wrap;
    
}
.item{
    min-width: 20%;
    background-color: aquamarine;
    border-radius: 5px;
    padding: 5px;
    margin: 10px;
}
</style>
