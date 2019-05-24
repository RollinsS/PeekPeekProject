<template>
     
          <div> Location
              <div class="container">
                  <div v-on:click="addLocation('Los Angeles')">Los Angeles</div>
                  <div v-on:click="addLocation('Orange County')">Orange County</div>
                  <div v-on:click="addLocation('Riversie')">Riverside</div>
                  <div v-on:click="addLocation('Other')">Other</div>
              </div>
          </div>
        
</template>

<script>

export default {
  name: "Industry",

  methods: {
     addLocation(event) {
         this.$emit('clicked',{
             location: event
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

 
</style>


