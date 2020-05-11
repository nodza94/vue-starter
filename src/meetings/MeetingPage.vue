<template>
    <div>
        <div>
       <button>Dodaj Nowe spotkanie</button></div>
        <div>
       <new-meeting-form v-show="status = true" @added="addNewMeeting($event)"></new-meeting-form></div>
      
       <meetings-list :meetings="meetings"></meetings-list>
       <meetings-list :
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
    
  components: {NewMeetingForm, MeetingsList},
  data() {
      return {
          meetings: [],
          email: "",
          message: "",
          status: false
      };
  },
  methods: {
      addNewMeeting(meeting) {
          if (meeting.name == ''){
              message = "Spotkanie musi mieć nazwe";
          }
          this.meetings.push(meeting);

      },
      addParticipant(meeting, email){
          this.meeting.participants.push(email);
      },
       statusChange() {
          this.status = true;
      }
      
  }  
  

}
</script>