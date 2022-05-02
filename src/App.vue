<template>
<NewHeader/>
<div class="container">
    <router-view/>
</div>
</template>

<script>
import NewHeader from '@/components/NewHeader.vue'
export default {
  components: { 
   NewHeader
  }
  
}
</script>

<style>



</style>
