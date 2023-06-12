<script>
  import Header from "$lib/Header.svelte"
  import Footer from "$lib/Footer.svelte"

  let index = " "
  let computerPlay = " "
  let usersPlay = " "
  let userStatus = " "
  let actions = ["paper", "scissors", "rock"]

  function paperSelect() {
    usersPlay = "paper"
  }
  function scissorSelect() {
    usersPlay = "scissor"
  }
  function rockSelect() {
    usersPlay = "rock"
  }
  function runGame() {
    index = " "
    computerPlay = " "
    usersPlay = " "
    userStatus = " "
    index = Math.floor(Math.random() * 3)
    computerPlay = actions[index]
    if ((usersPlay = "paper")) {
      if ((computerPlay = "scissors")) {
        userStatus = "You lost!"
      } else if ((computerPlay = paper)) {
        userStatus = "It was a draw"
      } else {
        userStatus = "You won!"
      }
    } else if ((usersPlay = "scissors")) {
      if ((computerPlay = "rock")) {
        userStatus = "You lost!"
      } else if ((computerPlay = "scissors")) {
        userStatus = "It was a draw"
      } else {
        userStatus = "You won!"
      }
    } else {
      if ((computerPlay = "paper")) {
        userStatus = "You lost!"
      } else if ((computerPlay = "rock")) {
        userStatus = "It was a draw"
      } else {
        userStatus = "You won!"
      }
    }
  }
</script>

<Header />

<main>


  <h2>Test your luck against the computer!</h2>
  <div class="columns"></div>
  <div class="column">
  <p>Computer played: {actions[index]}</p>
  <img src={computerPlay}>
</div>
<div class="column">
  <div class="buttons">
    <button
      on:click={() => {
        paperSelect()
        runGame()
      }}>Paper</button
    >
    <button
      on:click={() => {
        scissorSelect()
        runGame()
      }}>Scissors</button
    >
    <button
      on:click={() => {
        rockSelect()
        runGame()
      }}>Rock</button
    >
  </div>
</div>
</div>
  <p>{userStatus}</p>
</main>

<Footer />

<style>
  main {
    padding-left: 2%;
    height: 70vh;
  }

  h2 {
    font-style: italic;
    font-size: 160%;
    padding-bottom: 3%;
  }

  button {
    padding: 4%;
    margin-right: 2%;
    width: 15%;
    font-size: 140%;
  }

  .buttons {
    align-content: center;
    padding-left: 30%;
    padding-top: 20%;
  }
</style>
