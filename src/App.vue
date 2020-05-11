<template>
  <div>
    <h1>System do zapisów na zajęcia</h1>
    <div v-if="authenticatedUsername != ''">
      <h3 v-show="true">Witaj {{authenticatedUsername}}!</h3>
      <a @click="logMeOut()">Wyloguj</a>
      <meeting-page v-show="status = true" @click="addMeeting($event)"></meeting-page>

    </div>
    <div v-else>
      <login-form @login="logMeIn($event) "></login-form>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import MeetingPage from "./meetings/MeetingPage.vue";

export default {
  components: { LoginForm, MeetingPage },
  data() {
    return {
      email: "",
      authenticatedUsername: "",
      status: false
    };
  },
  methods: {
    logMeIn(username) {
      this.authenticatedUsername = username;
      this.status = false;
    },
    logMeOut() {
      this.authenticatedUsername = "";
    },
    
      statusChange() {
          this.status = !status;
         
      }
    
  }
};
</script>
