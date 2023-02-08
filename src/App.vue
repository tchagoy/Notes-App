<script setup>
import { ref } from "vue";

const showModal = ref(false);

//Using two-way binding; if state changes, view is updated. If view is updated,
//state changes.
const newNote = ref("");
const errorMessage = ref("");

const currentId = ref(0);

//Reference to all notes created
const notes = ref([]);

function getRandomColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const addNote = () => {
  const idNum = currentId.value;

  if (newNote.value.length < 10) {
    return (errorMessage.value = "A note needs to be 10 characters or more");
  }

  notes.value.push({
    id: idNum,
    text: newNote.value,
    date: new Date(),
    backgroundColor: getRandomColor(),
  });

  currentId.value++;
  showModal.value = false;
  newNote.value = "";
  errorMessage.value = "";
};
</script>

<template>
  <main>
    <div v-show="showModal" class="overlay">
      <div class="modal">
        <!-- v-mode directive for two-way binding -->
        <textarea
          v-model.trim="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <p v-if="errorMessage">{{ errorMessage }}</p>
        <button @click="addNote()">Add Note</button>
        <button class="close" @click="showModal = false">Close</button>
      </div>
    </div>

    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>

      <div class="cards-container">
        <div
          v-for="note in notes"
          :key="note.id"
          class="card"
          :style="{ backgroundColor: note.backgroundColor }"
        >
          <button class="close-button" data-close>
            <span aria-hidden="true">&times;</span>
          </button>
          <p class="main-text">
            {{ note.text }}
          </p>
          <p class="date">{{ note.date.toDateString() }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}

.container {
  max-width: 1000px;
  padding: 10px;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 75px;
}

header button {
  border: none;
  padding: 10px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  background-color: gray;
  border-radius: 100%;
  color: white;
  font-size: 20px;
}

.card {
  width: 225px;
  height: 225px;
  background-color: rgb(237, 182, 44);
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
  color: black;
}

.card .close-button {
  position: absolute;
  width: 10%;
  float: right;
  left: 85%;
  background-color: gray;
  border: none;
  border-radius: 20%;
}

.card .close-button:active {
  background-color: #3e8e41;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.card .close-button:hover {
  background-color: red;
}

.cards-container {
  display: flex;
  flex-flow: wrap;
}

.date {
  font-size: 12.5px;
  font-weight: bold;
  display: flex;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 750px;
  background-color: white;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.modal button {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: blueviolet;
  border: none;
  color: white;
  cursor: pointer;
  margin-top: 15px;
}

.modal textarea {
  padding: 10px;
}

.modal .close {
  background-color: rgb(193, 15, 15);
  margin-top: 7px;
}

.modal p {
  color: red;
}
</style>
