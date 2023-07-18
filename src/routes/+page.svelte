<script>
  import Header from "$lib/Header.svelte"
  import Footer from "$lib/Footer.svelte"
  //Default Variables
  let index = " "
  let source = "placeholder.png"
  let computerImage = "placeholder.png"
  //Outcome is set to default "Press Button"
  let resultIndex = 3
  const numberOfChoices = 3
  let computerPlay = " "
  let usersPlay = " "
  let actions = ["paper", "scissors", "rock"]
  let results = ["You Won!", "You Lost", "It was a draw", "Press a button to start!"]

  //These functions apply the user's choice to the usersPlay variable and then start the game.
  function paperSelect() {
    usersPlay = "paper"
    source = "paper.png"
    runGame()
  }
  function scissorSelect() {
    usersPlay = "scissors"
    source = "scissors.png"

    runGame()
  }
  function rockSelect() {
    usersPlay = "rock"
    source = "rock.png"
    runGame()
  }

  function runGame() {
    //Computer selects a random play from the array
    computerPlay = " "
    index = Math.floor(Math.random() * numberOfChoices)
    computerPlay = actions[index]
    computerImage = computerPlay + ".png"
    //Compares user play to computer play and selects appropriate outcome.
    if (usersPlay == "paper") {
      if (computerPlay == "rock") {
        resultIndex = 0
        console.log("You Won")
      } else if (computerPlay == "scissors") {
        resultIndex = 1
        console.log("You lost")
      } else {
        resultIndex = 2
        console.log("it was a draw")
      }
    } else if (usersPlay == "scissors") {
      if (computerPlay == "paper") {
        resultIndex = 0
        console.log("You Won")
      } else if (computerPlay == "rock") {
        resultIndex = 1
        console.log("You lost")
      } else {
        resultIndex = 2
        console.log("it was a draw")
      }
    } else {
      if (computerPlay == "scissors") {
        resultIndex = 0
        console.log("You Won")
      } else if (computerPlay == "paper") {
        resultIndex = 1
        console.log("You lost")
      } else {
        resultIndex = 2
        console.log("it was a draw")
      }
    }
  }
</script>

<Header />

<main>
  <h2>Test your luck against the computer!</h2>
  <div class="columns">
    <div class="column">
      <p>You Played: {usersPlay}</p>
      <img src={source} alt="" />
    </div>
    <div class=" column">
      <p class="result">{results[resultIndex]}</p>
      <div class="buttons">
        <button on:click={paperSelect}>Paper</button>
        <button on:click={scissorSelect}>Scissors</button>
        <button on:click={rockSelect}>Rock</button>
      </div>
    </div>
    <div class="column">
      <p>Computer Played: {computerPlay}</p>
      <img src={computerImage} alt="" />
    </div>
  </div>
</main>

<Footer />

<style>
  main {
    padding-left: 2%;
    height: 70vh;
    padding-right: 2%;
  }

  h2 {
    font-style: italic;
    font-size: 160%;
    padding-bottom: 3%;
    text-align: center;
    font-family: "Orbit", sans-serif;
  }
  p {
    padding-bottom: 4%;
    font-family: "Orbit", sans-serif;
  }
  img {
    width: 50%;
    z-index: 2;
  }

  .result {
    text-transform: uppercase;
    font-weight: bold;
    font-size: 260%;
    padding-top: 10%;
    font-family: "Orbit", sans-serif;
    text-shadow: 3px 2px rgb(128, 125, 125);
  }

  .column {
    text-align: center;
  }
  .buttons {
    width: 30%;
    justify-content: space-between;
    position: absolute;
    padding-top: 5%;
  }
  button {
    padding: 3%;
    font-size: 150%;
    font-family: "Orbit", sans-serif;
    background-color: white;
  }
</style>
