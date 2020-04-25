<template>
  <div>
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <div v-if="authenticatedUsername != ''">
    <!-- <h1>Twój email to: {{ email }}</h1> -->
    <h3 v-if="true">Witaj {{authenticatedUsername}}</h3>
    <a @click="logMeOut()">Wyloguj</a>
    </div>
    <div v-else>
      Zaloguj się e-mailem 
    <input type="text" v-model="email">
    <button @click="logMeIn()">Zaloguj</button>
    
    </div>
<!-- <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za długi.</div>
    -->
    
  </div>
</template>

<script>


export default {
 data() {
  return {
    email: '',
    authenticatedUsername: ''
  };
 },
 methods: {
   logMeIn (){
     this.authenticatedUsername = this.email;   
     this.email = '';  
   },
   logMeOut (){
     this.authenticatedUsername = '';
     
   }

 }
};
</script>
