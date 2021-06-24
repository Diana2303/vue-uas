<template>
  <div class="p-1" style="background-color: darkturquoise; width: 1349px">
    <div class="bg-red-500 w-1/2 border-2 border-gray-400 my-14 px-20 pt-10 mx-auto" style="width: 1150px" id="app">
      <div class="justify-center flex items-center font-bold bg-green-500 shadow-lg text-gray-200 h-20 text-3xl mx-auto mb-10" style="width: 310px">Khasus Covid 19</div>
      <table class="w-full mb-16 mt-16">
        <tr>
          <th class="border-t-2 border-l-1 border-b-2 border-red-500 bg-blue-200 text-black text-lg font-semibold text-center p-3">#</th>
          <th class="border-2 border-red-500 bg-blue-200 text-black text-lg font-semibold text-center">Negara</th>
          <th class="border-2 border-red-500 bg-blue-200 text-black text-lg font-semibold text-center">Khasus</th>
          <th class="border-2 border-red-500 bg-blue-200 text-black text-lg font-semibold text-center">Sembuh</th>
          <th class="border-2 border-red-500 bg-blue-200 text-black text-lg font-semibold text-center">Meninggal</th>
        </tr>    
        <tbody>
          <tr v-for="(item, tabel) in data.Countries" :key="tabel" class="border-b-2 border-red-500">
          <th class="border-1 border-red-500 bg-blue-200 text-black text-lg font-thin text-center pt-2">{{ tabel }}</th>
          <td class="border-2 border-red-500 text-black text-lg font-thin bg-blue-200 text-center">{{ item.Country }}</td>
          <td class="border-2 border-red-500 text-black text-lg font-thin bg-blue-200 text-center">{{ item.TotalConfirmed }}</td>
          <td class="border-2 border-red-500 text-black text-lg font-thin bg-blue-200 text-center">{{ item.TotalRecovered }}</td>
          <td class="border-2 border-red-500 text-black text-lg font-thin bg-blue-200 text-center">{{ item.TotalDeaths }}</td>
          </tr> 
        </tbody>       
      </table> 
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        countries: {},
        data: {},
        confirmed: 0,
        deaths: 0,
        recovered: 0,        
      }
    },
    
    mounted() {
      this.getCountries();
      this.getDataCovid()
    },

    methods: {
      getDataCovid() {
        axios
          .get('https://api.covid19api.com/summary')
          .then(response => { const data = response.data;
            this.data = data;
            this.confirmed = data.Global.TotalConfirmed;
            this.deaths = data.Global.TotalDeaths;
            this.recovered = data.Global.TotalRecovered;})
      },
      getCountries(){
        axios
          .get('https://api.covid19api.com/countries')
          .then(response => { this.countries = response.data;})
      }
    }
  }
</script>

<style>
    
</style> 