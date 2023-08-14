<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>Asset name</th>
          <th>Department</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Printer</td>
          <td>HR</td>
        </tr>
        <tr>
          <td>Monitor</td>
          <td>IT</td>
        </tr>
        <tr>
          <td>Barcode Scanner</td>
          <td>ACCOUNT</td>
        </tr>
      </tbody>
    </table>
    <br>
    <button @click="downloadCSV()">Download Table</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tableData: [
        {
          col1: "Asset name",
          col2: "Department"
        },
        {
          col1: "Printer",
          col2: "HR"
        },
        {
          col1: "Monitor",
          col2: "IT"
        },
        {
          col1: "Barcode Scanner",
          col2: "Account"
        }
      ]
    }
  },
  methods: {
    downloadCSV () {
      const csvData = this.tableData.map(asset => `${asset.col1},${asset.col2}`).join("\n");
      const blob = new Blob([csvData], {type: "text/csv"});
      const link = document.createElement("a");
      link.href = window.URL.createObjectURL(blob);
      link.download = "table.csv";
      link.click();
    }
  }
};
</script>

<style>
body {
  background-color: #FFF;
}

table, th, td {
  border: 2px solid black;
  border-collapse: collapse;
}

th, td {
  color: black;
  padding: 5px 10px;
}

th {
  text-align: left;
}

table {
  table-layout: fixed;
  width: 500px;
}
</style>
