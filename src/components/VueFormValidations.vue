<template>
      <v-container>
        <center>
            <form @submit.prevent="submitForm" class="form">
                <h1>Vuelidate Validations</h1>
                <div class="form-group">
                    <label>Name</label>
                    <input type="text" v-model="name" class="form-control" required @blur="$v.name.$touch()">
                    <span v-if="!$v.name.required && $v.name.$dirty" class="text-danger">Name is Required!</span>
                    <span v-if="!$v.name.minLength && $v.name.$dirty" class="text-danger">Minimum {{$v.name.$params.minLength.min}} characters should required!</span>
                    <span v-if="!$v.name.maxLength && $v.name.$dirty" class="text-danger">Characters should not exceed {{$v.name.$params.maxLength.max}} </span>
                    <!-- <span v-if="!$v.name.minLength && $v.name.$dirty" class="text-success">Valid Name</span> -->
                    <!--     -->
                    <!-- <span >Minimum lentght is 5 Characters</span> -->
                </div>

                <div class="form-group">
                    <label>Email</label>
                    <input type="email" v-model="email" class="form-control" required @blur="$v.email.$touch()">
                    <span v-if="!$v.email.required && $v.email.$dirty" class="text-danger">This field is required</span>
                    <span v-if="!$v.email.email" class="text-danger">Valid Email is Required</span>
                    <span v-if="!$v.email.maxLength && $v.email.$dirty" class="text-danger">Maximum {{$v.name.$params.maxLength.max}} characters should required!</span>
                    <!-- <span v-if="(!$v.email.required || $v.email.email) && $v.email.$dirty" class="text-danger">Valid Email is Required</span> -->
                    <!-- <span v-if=" $v.email.email && $v.email.$dirty" class="text-success">Valid Email</span> -->
                    
                </div>

                <div class="form-group">
                    <label>Password</label>
                    <input type="password" v-model="password" class="form-control">
                    <span v-if="!$v.password.required && $v.password.$dirty" class="text-danger">Password is Required</span>
                    <span v-if="(!$v.password.minLength || !$v.password.maxLength ) && $v.password.$dirty" class="text-danger">Password must be between {{$v.password.$params.minLength.min}} to {{$v.password.$params.maxLength.max}} characters</span>
                </div> 

                <div class="form-group">
                   <label for="">Gender</label>
                   <select v-model="gender" class="form-control" >
                    <option value="" disabled >Select Gender</option>
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                    <option value="other">Other</option>
                   </select>
                   <span v-if="!$v.gender.required && $v.gender.$dirty" class="text-danger">Gender is required!</span>
                </div> 

                 <div class="form-check mt-2">
                     <input type="checkbox" v-model="acceptTerms" class="form-check-input">
                     <label for="" class="form-check-label">Accept Terms & Conditions</label>    
                 </div>
                 <span v-if="!$v.acceptTerms.required && $v.acceptTerms.$dirty" class="text-danger">Accept terms is required</span> <br>
                 <input type="submit" class="btn btn-primary mt-3">
            </form>
        </center>
      </v-container>
      <!-- Reference:-https://www.youtube.com/watch?v=DCD0NoSuqdc -->
</template>

<script>
// import useValidate from 'vuelidate/core'
import { required, minLength, maxLength, alpha, email } from 'vuelidate/lib/validators'


export default {
      name:'VueformValidations',
      data(){
        return{
            // v$: useValidate(),
            name:'',
            email:'',
            password:'',
            gender:'',
            acceptTerms:'',
        }
      },
      validations:{
           name:{
              required,
              alpha,
              minLength:minLength(4),
              maxLength:maxLength(10),
           },
           email:{
              required,
              email,
              maxLength:maxLength(20)
           },
           password:{
              required,
              minLength:minLength(4),
              maxLength:maxLength(10),              
           },
           gender:{
              required,
           },
           acceptTerms:{
              required,
           }
      },
       methods:{
           submitForm(){
               this.$v.$touch();
            //    this.v$.validate()

               if(this.$v.$invalid){
                   console.log(`Name: ${this.name} Email:-${this.email} Gender:- ${this.gender} Password:- ${this.password} AcceptTerms:- ${this.acceptTerms} `)
               }
           }
       }

}
</script>

<style scoped>
      .form{
     max-width: 600px;
     border: 1px solid grey;
     border-radius: 5px;
     box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
     background-color: white;
     text-align: left;
     padding: 15px;
  }

</style>