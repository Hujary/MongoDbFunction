<template>
  <div>
    <input v-model="message" placeholder="edit me" />
    <button @click="axiosApiCall">  Press me  </button>
  </div>
</template>

<script>
import axios from 'axios'

export default{
  name: 'HelloWorld',
  data(){
    return{
      message: ""
    }
  },
  methods: {
   async axiosApiCall(){

        // GET Request
     //await axios.get('https://mongodbworkshop.azurewebsites.net/api/testfunction?name=tom').then((response) => {
     // let info = response
     //  console.log(info);
     //})


        // Post Request
    await axios.post('https://mongodbworkshop.azurewebsites.net/api/testfunction', {
      name: this.message,
    }).then((response) => {
       let info = response
       console.log(info);
     })

    }
  }
}
</script>

<style scoped>
</style>
