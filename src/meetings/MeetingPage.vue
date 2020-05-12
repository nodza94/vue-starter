<template>
    <div>
	   <button v-if="!meetingBeingAdded" @click="meetingPossible()">Dodaj Nowe spotkanie</button>
       <new-meeting-form v-else @added="addNewMeeting($event)"></new-meeting-form>
       <div v-show="meetings.length == 0">
        <h5>Brak zaplanowanych spotkań </h5>
        </div>
       <meetings-list :meetings="meetings" :user="user"></meetings-list>

    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";
export default {
  components: {NewMeetingForm, MeetingsList},
  props: ['user'],
  data() {
      return {
		  meetings: [],
          meetingBeingAdded: false
      };
  },
  methods: {
	  addNewMeeting(meeting) {
          this.meetings.push(meeting); 
          this.meetingBeingAdded=false;
          
          },
	  meetingPossible() {
          this.meetingBeingAdded=true;
          }
  }
}
</script>