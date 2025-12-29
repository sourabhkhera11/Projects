<script lang="ts">
  type fetchDataType=Array<{name: string, unicodeFlag: string}>;
  import { defineComponent } from 'vue';
  import card from "./components/card.vue";
  export default defineComponent({
    components:{
      card
    },
    data: function(){
      return{
        fetchData:[] as fetchDataType,
      };
    },
    methods:{
      async fetchCountries(){
        try{
          const response= await fetch("https://countriesnow.space/api/v0.1/countries/flag/unicode");
          const data=await response.json();
          this.fetchData=data.data;
        }
        catch(error){
          console.log(error);
        }
      }
    },
    mounted(){
      this.fetchCountries();
    }
  })
</script>

<template>
  <div class="container">
    <h1>Flags with country name!</h1>
    <div class="feed">
      <div class="cards" v-for="(value,index) in fetchData" :key="index">
        <card :flag="value.name" :cname="value.unicodeFlag" />
      </div>
    </div>
  </div>
</template>

<style scoped>
  *{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .container{
    margin: 50px;
  }
  .feed{
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    margin:20px;
    margin-top:50px;
  }
  .cards{
    width: 25%;
    border: 1px solid black;
  }
</style>
