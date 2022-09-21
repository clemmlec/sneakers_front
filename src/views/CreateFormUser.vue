<template>
  <div class="container">
    <br>
    <div style="color: black; background-color: #e2e1e1; border-radius: 10px; padding: 20px">
      <h3>Formulaire</h3>
      <form class="row g-3 needs-validation" novalidate>
        <div class="col-md-4">
          <label for="validationCustom01" class="form-label">email</label>
          <input v-model='user.email' type="text" class="form-control" id="validationCustom01" required>
          <div class="valid-feedback">
            Looks good!
          </div>
        </div>
        <div class="col-md-4">
          <label for="validationCustom02" class="form-label">password</label>
          <input v-model='user.password' type="text" class="form-control" id="validationCustom02" required>
          <div class="valid-feedback">
            Looks good!
          </div>
        </div>
       
        <div class="col-12">
          <br>
          <button @click='handleSaveBtn' class="btn btn-primary" type="button">Create or Edit</button>
        </div>
      </form>
    </div>
    <br>
  </div>
</template>

<script>
 import axios from 'axios'

  const API_SNEAKERS = 'https://127.0.0.1:8000/login_check';

  export default {
    name: 'CreateForm',
    data:()=>({
        // mangaType:['Seinen','Josei','Shojo'],
        user:{
          email:'',
          password:'',
        },
       
    }),
    methods:{
     async handleSaveBtn(){
       
          await this.login()
       
      },
     
      async login(){
        console.warn('ici en login')
        const log = await axios.post(API_SNEAKERS ,
          this.user,
       );

       localStorage.setItem('JWT', log.data.token);
        
        //local storage
        // console.log(log.data.token)
      }

    },
    
  }
  </script>