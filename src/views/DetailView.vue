<template>
     <button class="bg-green-700 text-white rounded py-2 px-3 focus:outline-none">
       <router-link to="/">
        Go Back
       </router-link>
     </button>

    <div class="bg-gray-600">
      <div class="flex justify-around flex-wrap">
        <div
          class="
            px-2
            py-1
            box-border
            w-full
            sm:w-1/3
            md:w-34
            h-20
            m-4
            bg-black
            text-white
          "
        >
          <div class="flex justify-between">
            <p>Total</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.TotalConfirmed }}</h3>
          </div>
        </div>
        <div
          class="
            px-2
            py-1
            box-border
            w-full
            sm:w-1/3
            md:w-28
            h-20
            m-4
            bg-black
            text-white
          "
        >
          <div class="flex justify-between">
            <p>Recovered</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.TotalRecovered }}</h3>
          </div>
        </div>
        <div
          class="
            px-2
            py-1
            box-border
            w-full
            sm:w-1/3
            md:w-28
            h-20
            m-4
            bg-black
            text-white
          "
        >
          <div class="flex justify-between">
            <p>Death</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.TotalDeaths }}</h3>
          </div>
        </div>
        <div
          class="
            px-2
            py-1
            box-border
            w-full
            sm:w-1/3
            md:w-28
            h-20
            m-4
            bg-black
            text-white
          "
        >
          <div class="flex justify-between">
            <p>Active</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.NewConfirmed }}</h3>
          </div>
        </div>
        <div
          class="
            px-2
            py-1
            box-border
            w-full
            sm:w-1/3
            md:w-28
            h-20
            m-4
            bg-black
            text-white
          "
        >
          <div class="flex justify-between">
            <p>New</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.NewDeaths }}</h3>
          </div>
        </div>
        <div
          class="px-2 py-1 w-full sm:w-1/3 md:w-28 h-20 m-4 bg-black text-white"
        >
          <div class="flex justify-between">
            <p>Country</p>
            <div>
              <i class="fa fa-arrow-up"></i>
            </div>
          </div>
          <div class="text-center">
            <h3>{{ country.Slug }}</h3>
          </div>
        </div>
      </div>
      <Inner :countries='countries'/>
    </div>
    
</template>

<script>
import Inner from '@/components/DetailViewCom'
export default {
  props: ["id"],
  components:{ 
  Inner
  },
  data() {
    return {
      country: {},
      countries: [],
    };
  },

  created() {
    this.country = this.$store.state.country;
    this.countries = this.$store.state.countries
    console.log(this.$store.state.country);
    console.log(this.country);
    console.log(this.countries);
  },
};
</script>

<style scooped>
.menu {
  height: calc(100vh -126px);
}
</style>