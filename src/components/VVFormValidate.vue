<template>
      <v-app>
          <v-container class="form">
               <v-form ref="signUpForm" v-model="formValidity" @submit.prevent="submitForm">
                            <h1 class="text center">Vuetify Vuelidate Register Form</h1>
                            <hr>
                            <v-text-field label="Title" v-model="title" :rules="titleRule" required ></v-text-field>

                            <v-text-field label="Firstname" v-model="firstName" ></v-text-field>

                            <v-text-field label="Lastname" v-model="lastName"></v-text-field>

                            <v-text-field label="Email" type="email" v-model="email" :rules="emailRule" required ></v-text-field>

                            <v-text-field label="Mobile Number" type="number" v-model="mobileNumber" ></v-text-field>

                            <v-text-field label="Organization" v-model="organization" ></v-text-field> 

                            <v-text-field label="Designation" v-model="designation" ></v-text-field>    

                            <v-text-area label="Address" v-model="address" ></v-text-area>

                            <v-text-field label="Password" v-model="password" ></v-text-field>

                            <v-text-field label="Confirm Password" v-model="confirmPassword" ></v-text-field>                      

                            <v-autocomplete label="Which browser you use?" :items="browers" ></v-autocomplete>

                            <v-file-input  label="Attach Profile picture" v-model="files"  required></v-file-input>

                            <v-text-field v-model="dob" label="DOB" readonly></v-text-field>

                            <v-date-picker v-model="dob" type="date" class="datePicker"  ></v-date-picker>

                            <v-checkbox label="Agree to terms & conditions" v-model="agreeToTerms" :rules="agreeToTermsRules" required ></v-checkbox>

                            <v-btn class="mr-4" type="submit" color="primary" :disabled="!formValidity"  >Submit</v-btn>
                            <v-btn color="success" class="mr-4" @click="validateForm">Validate Form</v-btn>
                            <v-btn class="mr-4" color="warning" @click="resetValidation" >Reset Validation</v-btn>
                            <v-btn color="error" @click="reset">Reset</v-btn>
                       </v-form>
          </v-container>
      </v-app>
</template>

<script>
import { required } from 'yargs'

export default {
       name:'VVFormValidate',
       data(){
          return{
              formValidity:false,              
              browers:['Chrome','Firefox','Safari','Edge','Brave'],
              title:'',
              titleRule:[
                  required
              ],
              firstName:'',
              lastName:'',
              email:'',
              emailRule:[
                required
              ],
              mobileNumber:'',
              organization:'',
              designation:'',
              address:'',
              password:'',
              confirmPassword:'',
              files:'',
              dob:'',
              date:'',
              agreeToTerms:false,
              agreeToTermsRules:[
                required
              ]

          }
       },
        submitForm(){
            alert('Submitted Successfully')
            console.log(`The submitted Form Data is ${this.title} ${this.firstName} ${this.lastName} ${this.email} ${this.mobileNumber} ${this.organization} ${this.designation} ${this.address} ${this.password} ${this.confirmPassword} ${this.files} ${this.dob} ${this.date} ` )
        },
        validateForm(){
            this.$refs.signUpForm.validateForm()
        },
        resetValidation(){
            this.$refs.signUpForm.resetValidation()
        },
        reset(){
            this.$refs.signUpForm.reset()
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
  }

  .datePicker{
     max-width: 300px;
  }

</style>