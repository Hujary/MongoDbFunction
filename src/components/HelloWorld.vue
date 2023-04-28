<template>
  <div>
    <input v-model="inputEmail" placeholder="enter your Email" />
    <input v-model="inputName" placeholder="enter your Name" />
    <button @click="axiosApiCall">  Press me  </button>
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

    }).then((response) => {
       let info = response
       console.log(info);
       let data = info.data;
       console.log(data);
     })

    }
  }
}
</script>

<style scoped>
</style>
