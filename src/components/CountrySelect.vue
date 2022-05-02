<template>
 <select 
 @change="change"
 v-model="selected"
  class="form-select mt-10 pl-4 text-2xl block w-full h-10 border-2 border-blue-200 rounded focus:bg-gray-200 focus:border-blue-300">
     <option value="0">Select Country</option>
     <option  v-for="(country,index) in countries"  :value="country.ID" :key="index" >
         {{country.Country}}
     </option>
 </select>
</template>

<script>
export default {
 name:'CountrySelect',
 props:['countries'],
 data(){ 
     return{ 
         selected:0
     }
 },
 methods: { 
     change(){ 
         const country = this.countries.find(item => item.ID === this.selected)
         console.log(country)
         this.$emit('get-country',country)
         this.$store.state.country = country
     }
 },
 unmounted(){ 
     this.$store.state.countries = this.countries
 }
}
</script>

<style>

</style>