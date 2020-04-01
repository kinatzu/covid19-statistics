<template class="tablePage">
  
    <v-simple-table fixed-header height="6000px">
      <template v-slot:default>
        <thead class="headTable">
          <tr>
            <th class="text-left">Country</th>
            <th class="text-left">Total</th>
            <th class="text-left">New</th>
            <th class="text-left">Deaths</th>
            <th class="text-left">New</th>
            <th class="text-left">Recovered</th>
          </tr>
        </thead>
        <tbody class="tbodyT">
          <tr  v-for="item in data" :key="item.name">
            <td><strong>{{ item.country }}</strong></td>
            <td>{{ item.cases.total }}</td>
            <td><v-chip>{{ item.cases.new }}</v-chip></td>
            <td class="deaths">{{ item.deaths.total }}</td>
            <td><v-chip class="deathChip">{{ item.deaths.new }}</v-chip></td>
            <td><v-chip class="coverChip">{{ item.cases.recovered }}</v-chip></td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>

</template>

<script>
  export default {
    name: 'HelloWorld',
    data: function () {
    return {
      data: []
    };
  },
  mounted() {
    const _ = this;
    fetch("https://covid-193.p.rapidapi.com/statistics", {
      method: "GET",
      headers: {
        "x-rapidapi-host": "covid-193.p.rapidapi.com",
        "x-rapidapi-key": "da232c81f7mshd5461ae68686da7p184020jsnc3d48c69fe0a"
      }
    })
      .then(data => data.json())
      .then(result => {
        let sortedData = result.response.sort((a,b) => {
          return (b.cases.active > a.cases.active) ? 1 : -1
        });
        this.data = sortedData
      })
      .catch(err => {
        console.log(err);
      });
  }
  }   
</script>

<style>
.text-left{
  font-weight: bold !important;
  font-size: 15px !important;
  font-family: 'Montserrat', sans-serif !important; 
}
.tbodyT{
  font-family: 'Montserrat', sans-serif !important; 
}
.deaths{
  color: red !important;
  font-weight: bold !important;
}
.headTable{
  background-color: black !important;
}
.tablePage{
 font-family: 'Montserrat', sans-serif !important; 
}
/* .v-data-table table {
  background-color: rgba(55, 71, 79, 0.075) !important;
} */
.deathChip{
  background-color: rgba(255, 0, 0, 0.643) !important;
  color: white !important;
}
.coverChip{
  background-color: rgba(38, 170, 38, 0.5) !important;
  color: white !important;
}
</style>
