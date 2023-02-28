<template>
  <header>
    <nav class="navbar">
      <div>{{ PageTitle.toLocaleUpperCase() }} </div>
    </nav>
  </header>

  <div class="main_content">
    <button @click="openModal">+</button>
    <div class="header">
      <h3>Take your Notes here</h3>
    </div>
    <div class="header-border margin">
      <div class="header add">
        <p>Add a Note</p>
        <textarea v-model.trim="note" name="note" id="note" cols="30" rows="10" v-model="note"></textarea>


        <div class="button">
          <button @click="addNote">Add Note</button>
        </div>
      </div>
    </div>

    <div class=" margin">
      <p class="notes">Your Notes</p>

    </div>

    <div class="display_note margin">
      <p v-if="!notes.length">Noting to show! Use "Add a Note"section above to add notes.</p>
    <div class="all_note">
      <div class="real-note" v-for="note in notes">
        <p>{{note.note}}</p>
        <p class="date">{{ note.date }}</p>
        <button class="btn">Close Note</button>
      </div>     
    </div>
    </div>


  </div>
</template>

<script setup>
import { ref } from 'vue'
let PageTitle = "Note App Taker"
let isModalOpen = ref(false)
const note = ref('')
const notes = ref([])

function openModal() {
  isModalOpen
}
function addNote() {
  const newNote = {
    note: note.value,
    date: new Date(),
    id: Math.random()

  }
  notes.value.push(newNote)
  note.value = ''
  console.log(notes.value)
}



</script>

<style scoped>
.main_content {
  display: flex;
  flex-direction: column;
  align-items: center;

}

.navbar {
  background-color: green;
  font-size: 40px;
  color: white;
  text-align: center;
}

.header {
  font-family: bolder;
  font-size: 20px;
  margin-top: 20px;
  margin-right: 34em;

}

button {
  background-color: green;
  color: white;
  border: none;
  padding: 5px 2em;
  margin-bottom: 20px;

}

.add {
  margin: 20px;
}

.header-border {
  border: 2px solid rgb(236, 226, 226);
}

.notes {
  margin-top: 20px;
  font-size: 30px;
  font-weight: 900;
  border-top: 1px dotted grey;
  border-bottom: 1px dotted grey;

}

.real-note {
  border: 2px solid rgb(206, 183, 183);
  width: 90%;
  margin-top: 10px;
  padding: 0.5em 5%;
  background-color: blue;
  color: white;
}
.real-note button{
  text-align: center;
  
}
.all_note{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 2em;
}

.margin {
  width: 80%;
}

textarea {
  position: relative;
  width: 60em;
  height: 50px;

}

.btn {
  margin-top: 20px;

}

.flex {
  display: flex;
}
</style>
