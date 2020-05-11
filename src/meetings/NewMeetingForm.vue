<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label for = "name">Nazwa</label>
            <input type="text" v-model="newMeeting.name" required>
  
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
              <span v-if="msg.name">{{msg.name}}</span>

            <button>Dodaj</button> 

        </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {},
          status: false,
          msg: [],
          name: ""
      };
  },
  watch: {
    name(value){
      this.name = value;
      this.validateName(value);
    }
  },
  methods: {
      addNewMeeting() {
        this.$emit('added', this.newMeeting);
        if (this.newMeeting.name = ''){
      }
      else{
        this.newMeeting = {};

      }
    },
    removeMeeting(meeting){
        this.meeting.name = "0";
        
    },
    validateName(value){
      if (value.length == 0){
        this.msg['name'] = 'Spotkanie musi mieć nazwe';
      }
    }
  }
}
</script>