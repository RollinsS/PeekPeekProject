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
import $ from 'jquery';

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
          
          //as long as they have typed in a phone or email address then send the info
          if(event.phone != undefined || event.email != undefined){
              this.form.fname = event.fname;
              this.form.lname = event.lname;
              this.form.email = event.email;
              this.form.phone = event.phone;
              this.form.inquery = event.inquery;
 
            //send the data to email
            var data = {
            service_id: 'gmail',
                template_id: 'customer_info',
                    user_id: 'user_fff9Opb1hmekqqBL26773',
                        template_params: {
                        'first' : `${event.fname}`,
                        'last' : `${event.lname}`,
                        'email' : `${event.email}`,
                        'phone' : `${event.phone}`,
                        'industry' : `${this.form.industry}`,
                        'location' : `${this.form.location}`,
                        'inquery' : `${event.inquery}`
                        }
                        };

                        $.ajax('https://api.emailjs.com/api/v1.0/email/send', {
                        type: 'POST',
                        data: JSON.stringify(data),
                        contentType: 'application/json'
                        }).fail(function(error) {
                        alert('Oops... ' + JSON.stringify(error));
                        });
                
                //clear the form
          this.form.industry = " ";
          this.form.location = " ";
          this.form.fname = " ";
          this.form.lname = " ";
          this.form.email = " ";
          this.form.phone = " ";
          this.form.inquery= " ";


          }

          console.log(this.form.industry + " " +
          this.form.location + " " +
          this.form.fname + " " +
          this.form.lname + " " +
          this.form.email + " " +
          this.form.phone + " " +
          this.form.inquery);

           
      
      } //end of addToForm
}
}
    
</script>

<style scoped>
 
</style>


