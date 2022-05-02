<template>
  <div class="grid md:grid-cols-2 gap-4">
      <!-- Box1 -->
    
         <div class="shadow-lg bg-blue-100 p-10 text-center rounded">
         <h3 class="text-3xl text-blue-900 font-bold mb-4">
             Cases
         </h3>
         <div class="text-center">
              <div class="text-2xl mb-2">
             <span class="font-bold">New:</span>
          {{ numberWithCommas(stats.NewConfirmed)}}
         </div>
         <div class="text-2xl">
             <span class="font-bold">Total:</span>
          {{ numberWithCommas(stats.TotalConfirmed)}}
         </div>
         </div>
         <div class="flex flex-col items-start sm:items-center" v-if="stats.ID">
               <router-link :to="{name:'detail',params:{id:stats.Slug}}">
                   <button>
                       View Cases
                   </button>
               </router-link>
         </div>
     </div>
    

      <!-- Box2 -->
     <div class="shadow-lg bg-blue-200 p-10 text-center rounded">
         <h3 class="text-3xl text-blue-900 font-bold mb-4">
            Deaths
         </h3>
         <div class="text-center">
             <div class="text-2xl mb-2 ">
             <span class="font-bold">New:</span>
           {{numberWithCommas(stats.TotalConfirmed)}}
         </div>
         <div class="text-2xl">
             <span class="font-bold">Total:</span>
          {{numberWithCommas(stats.TotalDeaths)}}
         </div>
         </div>
     </div>
  </div>
</template>

<script>
export default {
name:'DataBoxes',
props:['stats'],
data(){ 
    return{ 
   
    }
},
methods: { 
    numberWithCommas(x){ 
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g,',')
    }
},
unmouted(){
    this.$store.state.country = this.stats
    console.log(this.$store.state.country);
}

  
    
}
</script>

<style>

</style>