<script>
  import Header from "$lib/Header.svelte"
  import Footer from "$lib/Footer.svelte"

  let index = " "
  let source = ""
  let resultIndex = " "
  let computerPlay = " "
  let usersPlay = " "
  let actions = ["paper", "scissors", "rock"]
  let results = ["You Won!", "You Lost", "It was a draw"]
  function paperSelect() {
    usersPlay = "paper"
    source = "paper.png"
    runGame()
  }
  function scissorSelect() {
    usersPlay = "scissor"
    source = "scissors.png"

    runGame()
  }
  function rockSelect() {
    usersPlay = "rock"
    source = "rock.png"
    runGame()
  }
  function runGame() {
    resultIndex = Number(resultIndex)
    computerPlay = " "
    index = Math.floor(Math.random() * 3)
    computerPlay = actions[index]
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
    } else if (usersPlay == "scissor") {
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
      if (computerPlay == "scissor") {
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
      <div class="buttons">
        <button on:click={paperSelect}>Paper</button>
        <button on:click={scissorSelect}>Scissors</button>
        <button on:click={rockSelect}>Rock</button>
      </div>
    </div>
    <div class="column">
      <img src={source} alt="" />
    </div>
    <div class="column">
      <p>Computer Played: {computerPlay}</p>
    </div>
  </div>

  <p>{results[resultIndex]}</p>
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
    text-align: center;
  }
</style>
