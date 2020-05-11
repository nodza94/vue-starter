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
               <td> <button>Zapisz się</button> </td>
               <td> <button>Usuń puste spotkanie</button> </td>
            </tr>
        </tbody>
    </table>
    <div v-show="meetings.length == 0">
        <h5>Brak zaplanowanych spotkań </h5>
        </div>
        </div>
</template>

<script>
export default {
    props: ['meetings'],
    data() {
      return {
          email: ""
      };
    },
    

      computed: {
  buttonOutLabelToDisplay() {
    return this.buttonLabel || 'Wypisz się';  
  }

      } 
}
</script>