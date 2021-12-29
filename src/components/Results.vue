<template>
  <div class="result">
    <ul v-for="item in list" :key="item.id">
      <button @click="deleteItem(item.id)" class="delete">×</button>
      <li>{{ item.title }}</li>
      <li>{{ item.amounts }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {};
  },
  methods: {
    deleteItem(id) {
      this.$emit("delItem", id);
    },
  },
};
</script>

<style scoped>
.result {
  padding-top: 50px;
  position: absolute;
  margin: 0 auto;
  width: 500px;
  left: 0;
  right: 0;
  padding-bottom: 50px;
}
.result ul {
  display: flex;
  list-style: none;
  width: 500px;
  background-color: #fff;
  padding: 10px 20px;
  border-radius: 10px;
  margin-bottom: 10px;
}
.result ul li {
  padding-right: 20px;
}
.result ul li:nth-child(1) {
  text-align: center;
}
.result ul li:last-child {
  padding-right: 0;
}
.result ul li:not(li:nth-child(1)) {
  width: 200px;
}
.result button {
  background: transparent;
  border: none;
  margin-right: 10px;
  padding: 5px 10px;
  text-align: center;
  color: red;
  font-weight: bold;
  cursor: pointer;
}
@media (max-width: 641px) {
  .result ul li:not(li:nth-child(1)) {
    width: initial;
  }
  .result ul {
    width: 350px;
  }
  .result {
    width: 350px;
  }
}
</style>
