<template>
  <form  @submit.prevent="handleSubmit"> <!-- event modifier -->
    <label for="email">Email:</label>
    <input type="text" id="email" required v-model="email">
    <label for="user-name">user name:</label>
    <input type="text" id="user-name" required v-model="userName">
    <label for="password">password:</label>
    <input type="password" id="password" required v-model="password">
    <div v-if="passwordError" class="error">{{  passwordError }}</div>
    

    <label for="Role">Role:</label>
    <select v-model="role">
        <option value="developer">Developer</option>
        <option value="designer">Designer</option>
    </select>


    <label >skills</label>
    <input type="text" v-model="tempSkill"  @keyup.alt="addSkill"><!-- the alt key allows to fire the event but without displaying the key-->
    <div v-for="skill in skills" :key="skill" class="pill"  ><!-- we need to add a key which is unique for each iteration-->
       <span @click="removeSkill(skill)">{{ skill }}</span> 
    </div>
    <div class="terms">
        <input type="checkbox" v-model="terms" required  > <!-- the v-model will be a boolean -->
        <label >accept term conditions</label>
    </div>

    <div class="submit">
    <button>Create an account</button>
  </div>

</form>

  <p>this is the user informations </p>
  <hr>
  <p>this the email : {{ email }}</p>
  <p>this is the user name : {{ userName }}</p>
  <p>this is the user password : {{  password }}</p>
  <p>this is the user Role : {{  role }}</p>
  <p>did the user accept the term : {{  terms }}</p>
  <p>the skills of the user : {{ skills }}</p>



 
</template>
<script>

// it is npm run serve not server you dumby
export default {
    data(){
        return {
            email:'',// this will take the value of the email field, using v-model 
            password:'',// it will track anychange of this informations 
            userName:'',// the v-model binds the data (getting the data)
            role:'', // we can set a default value fir the option and set role to be role:'full stack developer'
            terms:false,
            tempSkill: '', // listening to the keybord event
            skills:['talentless'],
            passwordError : ''
        }
    },
    methods:{
        addSkill(e){
            if(e.key == ',' && this.tempSkill){
                if(!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill)
            }
            this.tempSkill=''
        }
    },
    removeSkill(skill){
        const indexSkill = this.skills.indexOf(skill) // we get the index and then we remove the element using the splice function
        this.skills.splice(indexSkill,1)
        // or we can use the filter method 
    },
    handleSubmit(){
        // validate password 
        this.passwordError= this.password.length > 5 ?
         '' : 'Password must be at least 6 chars long'


         if(!this.passwordError){
            console.log('email : ' + this.email)
            console.log('password ' + this.password)
            console.log('Role ' + this.role )
         }
    }
}
// in the uppcoming days we would send this informations into a database and store it there 

}
</script >

<style scoped>
form{
    max-width: 420px;
    margin: 30px auto;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    background: white;
    position: relative;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
    width: 100%;
}
input , select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    color: #555;
    border: none;
    border-bottom: 1px solid #ddd;
    outline: none;
}

.terms{
    display: flex;
    align-items: center;
}

input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
    }
    .name{
        display: flex;
    }
    .pill{
        display: inline-block;
        margin: 20px 10px 0 0;
        padding: 6px 12px;
        background: #eee;
        border-radius: 20px;
        font-size: 12px;
        letter-spacing: 1px;
        font-weight: bold;
        color: #777;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
    }
    .pill:hover{
        background: #febdbd;
    }
    button{
        background: #1058c4;
        border: 0;
        font-size: 15px;
        font-weight: 400;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }
    .submit{
        text-align: center;
    }
    .error{
        color: #ff0062;
        margin-top: 10px;
        font-size: 0.8rem;
        font-weight: bold;
    }
</style>
<!-- the vue router 
different pages 
the vue router 

generate a new project-->
