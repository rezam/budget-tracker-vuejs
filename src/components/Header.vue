<template>
  <header>
    <h1>Budget Tracker</h1>
    <div class="total">{{ sum }}$</div>
  </header>
</template>

<script>
export default {
  props: ["sum"],
  data() {
    return {};
  },
};
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 40px;
  background-color: #313131;
  color: #fff;
  font-family: Poppins;
  border-bottom: 10px solid #a3423c;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.3);
}
header h1 {
  font-weight: normal;
  letter-spacing: 1px;
}
header .total {
  font-size: 2rem;
  background-color: #a3423c;
  padding: 5px 15px;
  border-radius: 10px;
  border: 5px solid #553b3a;
  text-shadow: 1px 2px #777;
}
@media (max-width: 641px) {
  header {
    display: flex;
    flex-direction: column;
  }
  header h1 {
    padding-bottom: 20px;
    font-size: 1.9rem;
  }
}
</style>
