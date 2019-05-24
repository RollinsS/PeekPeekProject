<template>
    <div class="container">Customer Info 
        
    <form @submit.prevent="creatForm(tempForm)">
    <label>
      <input placeholder="First Name" type="text" v-model="tempForm.fname"/>
    </label>
    <label>
      <input placeholder="Last Name" type="text" v-model="tempForm.lname"/>
    </label>
    <label>
      <input placeholder="Email" type="email" v-model="tempForm.email"/>
    </label>
    <label>
      <input placeholder="Phone" type="text" v-model="tempForm.phone"/>
    </label>
    <label>
      <textarea placeholder="Inquiry" type="text" v-model="tempForm.inquery"/>
    </label>
    
    <button type="submit"> Submit</button>
  </form>

    </div>
</template>

<script>
export default {
    data() {
    return {
    tempForm: {
          fname:'',
          lname:'',
          email:'',
          phone:'',
          inquery:'',
      },
    }
    },
    methods: {
        creatForm(form) {
            
            this.$emit('clicked',{
             fname: form.fname,
             lname: form.lname,
             email: form.email,
             phone: form.phone,
             inquery: form.inquery
         } )
        }
    }

}

</script>

<style scoped>
 .container {
    display: flex;
    align-content: space-around;
    padding: 5em 25em;
    margin: auto;
    background-color: lightgray;
}
input {
    margin: 2em 0;
}

</style>


