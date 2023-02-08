<template>
  <main>
    <div class="overlay"></div>

    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>

      <div class="cards-container">
        <div class="card">
          <p class="main-text">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Id quia
            tempora ad? Placeat, magnam accusantium!
          </p>
          <p class="date">04/27/2022</p>
        </div>

        <div class="card">
          <p class="main-text">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Id quia
            tempora ad? Placeat, magnam accusantium!
          </p>
          <p class="date">04/27/2022</p>
        </div>

        <div class="card">
          <p class="main-text">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Id quia
            tempora ad? Placeat, magnam accusantium!
          </p>
          <p class="date">04/27/2022</p>
        </div>

        <div class="card">
          <p class="main-text">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Id quia
            tempora ad? Placeat, magnam accusantium!
          </p>
          <p class="date">04/27/2022</p>
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

button {
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

.cards-container {
  display: flex;
  flex-flow: wrap;
}

.date {
  font-size: 12.5px;
  font-weight: bold;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.40);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>