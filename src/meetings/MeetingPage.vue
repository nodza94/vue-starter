<template>
    <div>
	   <button v-if="!meetingBeingAdded" @click="meetingPossible()">Dodaj Nowe spotkanie</button>
       <new-meeting-form v-else @added="addNewMeeting($event)"></new-meeting-form>
       <meetings-list :meetings="meetings"></meetings-list>
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
		  meetingBeingAdded: false
      };
  },
  methods: {
	  addNewMeeting(meeting) {this.meetings.push(meeting); this.meetingBeingAdded=false;},
	  meetingPossible() {this.meetingBeingAdded=true;}
  }
}
</script>