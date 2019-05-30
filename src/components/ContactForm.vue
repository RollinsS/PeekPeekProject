<template>
     <div>
        <component :is="this.formComponents" @clicked="addToForm($event)"></component>
        <!-- <Industry @clicked="addIndustry($event)"></Industry>
        <Location @clicked="addLocation"></Location> -->

     </div>
</template>

<script>

import Industry from './Industry.vue';
import Location from './Location.vue';
import CustomerInfo from './CustomerInfo.vue';

export default {
      name:"ContactForm",
      components: {
          Industry,
          Location,
          CustomerInfo
      },
    data() {
    return {
      form: {
          industry:'',
          location:'',
          fname:'',
          lname:'',
          email:'',
          phone:'',
          inquery:'',
      },
    formComponents: 'Industry',
    } 
  },
    
  methods: {
      addToForm(event){
          
          //adds to the form and loads the next component
          if(event.industry != undefined){
              this.form.industry = event.industry;
              this.formComponents = 'Location';
              console.log("adding an industry " + this.form.industry);
          }
          
          if(event.location != undefined){
              this.form.location = event.location;
              this.formComponents = 'CustomerInfo';
              console.log("adding a location " + this.form.location);
          }
          
          if(event.fname != undefined){
              this.form.fname = event.fname;
              this.form.lname = event.lname;
              this.form.email = event.email;
              this.form.phone = event.phone;
              this.form.inquery = event.inquery;
          }

          console.log(this.form.industry + "<br> " + this.form.location + "<br> " + 
              this.form.fname + " " +
              this.form.lname + " " +
              this.form.email + " " +
              this.form.phone + " " +
              this.form.inquery);
      }
}
}
    
</script>

<style scoped>
 
</style>


