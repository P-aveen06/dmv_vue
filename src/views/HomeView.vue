<script>
import Table from '../components/Table.vue'

export default {

  components:{
    Table
  },

  data() {
    return {
      userName: "Jhon Doe",
    };
  },
  watch: {
    userName(newValue) {
      localStorage.setItem("userName", newValue);
    },
  },
  created() {
    const storedValue = localStorage.getItem("userName");
    if (storedValue) {
      this.userName = storedValue;
    }
  },
  methods: {
    updateLocalStorage() {
      localStorage.setItem("userName", this.userName);
    },
  },
};
</script>


<template>
  <main>
    <section class="header-section">
      <h1>Hello,</h1>
      <input class='input' v-model="userName" @input="updateLocalStorage" />
    </section>
  </main>
  <Table></Table>
</template>

<style>
  .header-section{
    display: flex;
    gap: 1rem;
    align-items: center;
  }
  .input{
    height: 30px;
  }
</style>
