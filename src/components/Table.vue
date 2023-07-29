<template>
  <div class="table-section">
    <table>
      <thead>
        <tr>
          <th>Id</th>
          <th>Server Name</th>
          <th>Database Name</th>
          <th>Table Count</th>
          <th>Size</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" :key="item.id" @click="handleRowClick(item.id)">
          <td>{{ item.id }}</td>
          <td>{{ item.server_name }}</td>
          <td>{{ item.db_name }}</td>
          <td>{{ item.table_count }}</td>
          <td>{{ item.size }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
        const response = await fetch(
          "https://www.mockachino.com/4a0c8950-04b0-4b/api/table-data"
        );
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
        const data = await response.json();
        this.data = data.result;
    },

    handleRowClick(id){
        //navigate to svelte/diagram?selectedRow={id}
        console.log(id)
    }
  },
};
</script>

<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}

.table-section{
    margin: 1rem 2rem;
}

tr:hover{
    cursor: pointer;
}
</style>
