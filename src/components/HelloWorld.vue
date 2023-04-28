<template> 

  <div id="apps">
    
    <div id="login">
      <span id="text">Sign in</span>
      <input id="mail" v-model="inputEmail" placeholder="Email" />
      <input id="name" v-model="inputName" placeholder="Name" />
      <button id="send" @click="axiosApiCall">  Send Data  </button>
      <span>{{ this.confirmation }}</span>
    </div>

    <div id="list">
      <button @click="axiosGetCall"> Get all names </button>
      <p></p>
    </div>

  </div>

</template>

<script>
import axios from 'axios'

export default{
  name: 'HelloWorld',
  data(){
    return{
      inputEmail: "",
      inputName: "",
      postbool: "",
      confirmation: "",

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
       let type = response.data;
       this.postbool = type;
       console.log(this.postbool);
     })

     if(this.postbool==true){
      this.confirmation = "Daten wurden gespeichert";
     }else{
      this.confirmation = "Es gab einen Fehler";
     }

     this.inputEmail="";
     this.inputName="";

    },

    async axiosGetCall(){
      // Get Request
    await axios.get('https://mongodbworkshop.azurewebsites.net/api/testfunction').then((response) => {
      let data = response;
      console.log(data);
    })
    },


  }
}
</script>

<style>

#apps{
  display: flex;
  flex-direction: row;
}

#login{
  display: flex;
  flex-direction: column;
  width: 50%;
  height: 300px;
  padding-left: 150px;
}

#list{
  display: flex;
  flex-direction: column;
  width: 50%;
  height: 100%;
  padding-left: 200px;
}

#mail{
  padding-top: 10px;
  text-align: center;
  padding-bottom: 10px;
  margin-top: 70px;
}

#name{
  padding-top: 10px;
  text-align: center;
  padding-bottom: 10px;
  margin-top: 10px;
}

#send{
  height: 40px;
  margin-top: 20px;
}

#text{
  text-align: center;
  padding-top: 20px;
  font-size: xx-large;
}

</style>
