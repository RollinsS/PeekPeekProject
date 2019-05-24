<template>
     
     <div> Industry
         <div class="container">
         <div v-on:click="addIndustry('Education')"> </div>
         <div v-on:click="addIndustry('Hospitality')">Hospitality</div>
         <div v-on:click="addIndustry('Resturante')">Resturante</div>
         <div v-on:click="addIndustry('Other')">Other</div>
        </div>
         <!-- <b-container fluid>
             <b-row class="text-center">
                 <b-col cols="12">
                     Industry
                 </b-col>
             </b-row>
             <b-row class="text-center industryBlock">
                 <b-col id="box" v-on:click="addIndustry('Education')">Education</b-col>
                 <b-col id="box" v-on:click="addIndustry('Hospitality')">Hospitality</b-col>
                 <b-col id="box" v-on:click="addIndustry('Resturante')">Resturante</b-col>
                 <b-col id="box" v-on:click="addIndustry('Other')">Other</b-col>
             </b-row>
        </b-container> -->
     </div>
</template>

<script>

export default {
  name: "Industry",

  methods: {
     addIndustry(event) {
         this.$emit('clicked',{
             industry: event
         } )
     }
  }
}
</script>

<style scoped>
.container {
    display: flex;
    justify-content: space-between;
    padding: 5em;
    background-color: lightgray;
}
 /* .industryBlock {
     padding: 10em;
     background-color: lightgray;
 }
 #box {
     background-color: darkgray;
     margin: 0 2em;
 } */
 
 
</style>


