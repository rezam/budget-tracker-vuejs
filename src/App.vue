<template>
  <Header :sum="sum" />
  <user-input @submitData="getData"></user-input>
  <results :list="list" @delItem="deleteItem"></results>
</template>

<script>
import Header from "@/components/Header.vue";
import Results from "@/components/Results.vue";
import UserInput from "@/components/UserInput.vue";

export default {
  components: {
    Header,
    Results,
    UserInput,
  },
  data() {
    return {
      list: [],
      sum: 0,
    };
  },
  methods: {
    getData(title, amounts) {
      this.list.push({
        id: Date.now(),
        title: title,
        amounts: amounts,
      });
      this.sumAmounts();
    },
    deleteItem(id) {
      this.list = this.list.filter((item) => item.id !== id);
      this.sumAmounts();
    },
    sumAmounts() {
      this.sum = this.list
        .map((item) => item.amounts)
        .reduce((prev, curr) => prev + curr, 0);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@500&family=Poppins&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: Poppins;
  background-color: #ddd;
}
</style>
