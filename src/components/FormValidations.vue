<template>
       <v-container class="form">
              <v-row>
                  <v-col>
                       <v-form ref="signUpForm" v-model="formValidity" @submit="submitForm">
                            <h1 class="text center">Vue Custom Validations Submit Form</h1>
                            <hr>
                            <v-text-field label="Title" v-model="title" :rules="titleRule" required ></v-text-field>

                            <v-text-field label="Firstname" v-model="firstName" :rules="firstNameRule" required  ></v-text-field>

                            <v-text-field label="Lastname" v-model="lastName" :rules="lastNameRule" required  ></v-text-field>

                            <v-text-field label="Email" type="email" v-model="email" :rules="emailRule" required ></v-text-field>

                            <v-text-field label="Mobile Number" type="number" v-model.number="mobileNumber" :rules="mobileNumberRule" required ></v-text-field>

                            <v-text-field label="Organization" v-model="organization" :rules="organizationRule" required  ></v-text-field> 

                            <v-text-field label="Designation" v-model="designation" :rules="designationRule" required  ></v-text-field>    

                            <v-textarea label="Address" v-model="address" :rules="addressRule" required  ></v-textarea>

                            <v-text-field label="Password" v-model="password" :rules="passwordRule" required  ></v-text-field>

                            <v-text-field label="Confirm Password" v-model="confirmPassword" :rules="confirmPasswordRule" required  ></v-text-field>                      

                            <v-autocomplete label="Which browser you use?" :items="browers" ></v-autocomplete>

                            <v-file-input  label="Attach Profile picture" ></v-file-input>

                            <v-text-field v-model="dob" label="DOB" readonly></v-text-field>

                            <v-date-picker v-model="dob" type="date" class="datePicker"  ></v-date-picker>

                            <v-checkbox label="Agree to terms & conditions" v-model="agreeToTerms" :rules="agreeToTermsRules" required ></v-checkbox>

                            <v-btn class="mr-4" type="submit" color="primary" :disabled="!formValidity"  >Submit</v-btn>
                            <v-btn color="success" class="mr-4" @click="validateForm">Validate Form</v-btn>
                            <v-btn class="mr-4" color="warning" @click="resetValidation" >Reset Validation</v-btn>

                            <v-btn  color="error" @click="reset">Reset</v-btn>
                       </v-form>
                  </v-col>
              </v-row>
       </v-container>
</template>

<script>
export default {
    name:'FormValidations',
    data(){
        return{
            agreeToTerms:false,
            agreeToTermsRules:[
                value=> !!value || 'You should accept Terms and conditions for creating an account'
            ],
            title:'',
            titleRule:[
                value => !!value || 'Name is required',
                value => value.length >= 3 || 'Minimum length should be 3',
                value => value.lenght <=15 ||  'Maximum length should be 15',

            ],
            firstName:'',
            firstNameRule:[
                value => !!value || 'Name is required',
                value => value.length >= 3 || 'Minimum length should be 3',
                value => value.lenght <=15 ||  'Maximum length should be 15',
            ],
            lastName:'',
            lastNameRule:[
                value => !!value || 'Name is required',
                value => value.length >= 3 || 'Minimum length should be 3',
                value => value.lenght <=15 ||  'Maximum length should be 15',
            ],
            email:'',
            emailRule:[
                value => !!value || 'Email is required',
                value => value.indexOf('@') !== 0 || 'Email Should have a username.',
                value => value.includes('@') || 'Email should include an @ symbol.',
                value => value.indexOf('.') - value.indexOf('@') > 1 || 'Email should contain a valid domain.',
                value => value.indexOf('.') <= value.length - 3 || 'Email should contain a valid domain extension.'
                
            ],
            mobileNumber:null,
            mobileNumberRule:[
                value => !!value || 'Mobile Number is required',
                value => value.length >= 1 || 'Not a Valid Number',
                value => value.lenght <=10 || 'Not a Valid Number',
            ],
            organization:'',
            organizationRule:[
                value => !!value || 'This field is required',
                value => value.lenght <=15 ||  'Length Should not exceed 20 Characters',
            ],
            designation:'',
            designationRule:[
                value => !!value || 'This field is required',
                value => value.lenght <=15 ||  'Length Should not exceed 20 Characters',
            ],
            address:'',
            addressRule:[
                value => !!value || 'This field is required',
                value => value.length >= 3 || 'Minimum length should be 3',
                value => value.lenght <=15 ||  'Should not exceed 20 Characters',
            ],
            formValidity:false,
             dob:'',
             browers:['Chrome','Firefox','Safari','Edge','Brave'],
             
             
             
             
             
             password:'',
             confirmPassword:''

        }
    },
    methods:{
        submitForm(){
            alert('Form Submitted Successfully')
            console.log(`The submitted Form Data is ${this.title} ${this.firstName} ${this.lastName} ${this.email} ${this.mobileNumber} ${this.organization} ${this.designation} ${this.address} ${this.password} ${this.confirmPassword}`)
        },
         resetValidation(){
            this.$refs.signUpForm.resetValidation()
         },
         reset(){
            this.$refs.signUpForm.reset()  
         },
         validateForm(){
            this.$refs.signUpForm.validate()
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
  }

  .datePicker{
     max-width: 300px;
  }

</style>