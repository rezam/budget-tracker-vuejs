<template>
  <form @submit.prevent="sendData">
    <input
      @focus="changeStat"
      placeholder="Title..."
      type="text"
      name="title"
      v-model="title"
    />
    <input
      placeholder="amount..."
      type="number"
      name="amount"
      v-model="amount"
    />
    <button type="submit">submit</button>
  </form>
  <p v-if="errorStat" class="error">Please enter your income...</p>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      amount: "",
      errorStat: false,
    };
  },
  methods: {
    sendData() {
      if (this.title === "" || this.amount === "") {
        this.errorStat = true;
      } else {
        this.$emit("submitData", this.title, this.amount);
        this.title = "";
        this.amount = "";
      }
    },
    changeStat() {
      this.errorStat = false;
    },
  },
};
</script>

<style scoped>
.error {
  color: red;
  text-align: center;
  padding: 30px 30px;
  transition: all 0.3s;
}
form {
  padding-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}
form input {
  padding: 10px 17px;
  border: none;
  font-size: 18px;
  outline: none;
}
form input::placeholder {
  color: #aaa;
}
form input[type="text"] {
  border: none;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
  min-width: 300px;
}
input[type="number"] {
  -moz-appearance: textfield;
  appearance: textfield;
  margin: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
form button {
  padding: 9px 10px;
  cursor: pointer;
  background-color: #a3423c;
  color: #fff;
  font-family: Poppins;
  border: transparent;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  font-size: 16px;
  transition: all 0.3s;
}
form button:hover {
  background-color: #ae2a22;
}
form input::placeholder {
  font-family: Poppins;
}
@media (max-width: 641px) {
  form input[type="text"] {
    min-width: 50px;
  }
  form input[type="number"] {
    min-width: 50px;
  }
}
</style>
