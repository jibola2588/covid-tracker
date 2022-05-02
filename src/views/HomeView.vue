<template>
<main v-if="!loading">  
   <DataTitle :dataDate="dataDate" :text="title"/>
   <DataBoxes :stats="stats"/>
   <CountrySelect :countries="countries" @get-country="getCountryData" />
<button @click="clearCountryData"
v-if="stats.Country"
 class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:">
  Clear Country
</button>
</main>
<main class="flex flex-col items-center justify-center text-center"   v-else>
 <div class="text-gray-500 text-3xl mt-10 b-6">
  Fetching Data...
  <div class="mt-4 flex justify-center items-center">
    <img src="../assets/hourglass.gif" alt="" class="w-20 h-20">
  </div>
 </div>
</main>

</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'
export default {
  name: 'HomeView',
  components:{ 
   DataTitle,
   DataBoxes,
   CountrySelect
  },
  data(){ 
  return{ 
    loading:true,
    title:"Global",
    dataDate:'',
    stats:{},
    countries:[],
  }
  },
  methods: { 
    async getCovidData(){ 
     const res = await fetch('https://api.covid19api.com/summary');
     console.log(res)
     const data = await res.json()
     console.log(data)
     this.dataDate = data.Date
     this.stats = data.Global
     this.countries = data.Countries
     this.loading = false
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData(){ 
      this.loading = true;
     const data = await this.getCovidData('')
     this.title = 'Global'
     this.stats = data.Global
     this.loading = false
    }
  },
   created(){ 
     this.getCovidData()
   
  },
 unmounted(){ 
   this.$store.state.countries = this.countries
 }
}
</script>
