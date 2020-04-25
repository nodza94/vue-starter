<template>
  <div>
    <h1>Your email is: {{ email }}</h1>
    <input type="text" v-model="email">
    <div v-if="email.length < 10">Ale masz krótki adres!</div>
<div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
<div v-else>Twój adres e-mail jest stanowczo za d³ugi.</div>
  </div>
</template>

<script>


export default {
 data() {
  return {
    email: ''
  }
 }
};
</script>
