<template>
  <SignupForm></SignupForm>
</template>


<script>
import SignupForm from "./components/SignupForm"

export default {
  name: 'App',
  components: {
    SignupForm
  },
  data(){
    return {
     // ofc the return will be in the components file 
    }
  }
}

// data binding , how to get the data inputted by the user from an input firld in our component
</script>

<style>
/** WE ARE KEEPING THI STYLE FOR THE MOMENT  */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  margin: 0;
  padding: 0;
  background: #eee;
}

</style>
