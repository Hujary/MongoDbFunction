<template>
  <div id="login">
    <input v-model="inputEmail" placeholder="enter your Email" />
    <input v-model="inputName" placeholder="enter your Name" />
    <button @click="axiosApiCall">  Press me  </button>
  </div>
  <div>
    <button @click="axiosGetCall"> Get all names </button>
    <p></p>
  </div>
</template>

<script>
import axios from 'axios'

export default{
  name: 'HelloWorld',
  data(){
    return{
      inputEmail: "",
      inputName: ""
    }
  },
  methods: {
   async axiosApiCall(){
        // Post Request
    await axios.post('https://mongodbworkshop.azurewebsites.net/api/testfunction', {
      name: this.inputName,
      email: this.inputEmail, 

    }).then((response) => {
       let info = response;
       console.log(info);
     })

    },

    async axiosGetCall(){
      // Get Request
    await axios.get('https://mongodbworkshop.azurewebsites.net/api/testfunction').then((response) => {
      let data = response;
      console.log(data);
    })
    }

  }
}
</script>

<style scoped>

#login{
 
display: flex;
flex-direction: column;
width: 50%;
padding-left: 150px;

}

</style>
