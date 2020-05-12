<template>
<div>
    <h4>Zaplanowane zajęcia ({{meetings.length}})</h4>
    <table v-show="meetings.length > 0">
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td>{{ meeting.participants }}</td>

               <td><li v-for="participant in participants" :key="participant.id">{{ participant }}</li></td>
                <span v-if="participants.length == 0">
                    <td> <button @click="removeMeeting()">Usuń puste spotkanie</button> </td>
                    <td> <button @click="addParticipant()">Zapisz się</button> </td>
                </span>
                <span v-if="participants.length > 0 && participants.includes(this.newUser)">
                    <td> <button @click="removeParticipant()">Wypisz się</button> </td>
                </span>
                <span v-if="participants.length > 0 && !participants.includes(this.newUser)">
                     <td> <button @click="addParticipant()">Zapisz się</button> </td>
                </span>
            </tr>
        </tbody>
    </table>
   
        </div>
</template>

<script>
export default {
    props: ['meetings', 'user'],
    data() {
      return {
         participants: []
      };
    },
    
    methods: {
        removeMeeting(meetingNameToRemove){
             if(this.meetings.length >0){
            for(var i = 0;i < this.meetings.length; i++){
              if(this.meetings[i].name == meetingNameToRemove){
                  this.meetings.splice(i,1);
              }
            }
            }
            
          },
          addParticipant(){
              if(!this.participants.includes(this.user)) {
                  this.participants.push(this.user);
              }
          },
          removeParticipant(){
              this.participants.splice(this.participants.indexOf(this.user), 1);
          }
   
      } 
}
</script>