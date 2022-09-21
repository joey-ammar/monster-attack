<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Monster Attack</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>

    <main class="bg">
      <!-- The title contianer-->
      <div class="container">
        <small class="title"> Welcome to Monster Attack game</small>
      </div>
      <!-- The cards container-->
      <div class="cards">
          <div class="player">
              <div class="ball-player">
                <p>Player</p> <span></span>
              </div>
              <progress id="playersHealth" max="100" value="100">100</progress>
              <button id="playerAttaking">ATTACK</button>
              <button>Strong Attack</button>
              <button class="healPlayer">Heal</button>
          </div>
          <div class="monster">
              <div class="ball-monster">
                <p>Monster</p> <span></span>
              </div>
              <progress id="monstersHealth" max="100" value="100">100</progress>
              <button id="monsterAttacking">ATTACK</button>
              <button>Strong Attack</button>
              <button class="healMonster">Heal</button>
          </div>
      </div>
    </main>
    <script src="array.js"></script>
  </body>
</html>











/**
 * *********************
 * *********************
 * VARIABLES************
 * *********************
 * *********************
 */
/*PLAYER VARIABLES*/
const playerAttaking = document.querySelector('#playerAttaking');
let playersHealth = document.querySelector('#playersHealth');

/*MONSTER VARIABLES*/
const monsterAttacking = document.querySelector('#monsterAttacking');
let monstersHealth = document.querySelector('#monstersHealth');

/* ball */
const ballPlayer = document.querySelector(".ball-player span");
const ballMonster = document.querySelector(".ball-monster span");

/* Heal */
const healPlayer = document.querySelector(".healPlayer");
const healMonster = document.querySelector(".healMonster");


/* SETTING THE BTN TO DISABLE AS THE GAME BEGIN */
monsterAttacking.setAttribute("disabled", "");
ballPlayer.style.display = "flex";
ballMonster.style.display = "none"

/* RANDOM NUMBER ATTACK */
const randomNumberAttack = () => {
  return Math.floor(Math.random() * (15 - 0 + 1)) + 0;
}
/* RANDOM STRONG ATTACK */
const randomStrongAttack = () => {
  return Math.floor(Math.random() * (30 - 15) + 15);
}
/* RANDOM HEAL HEALTH*/
const randomHealHealth = () => {
  return Math.floor(Math.random() * (50 - 30) + 30);
}



/*WHEN PLAYER ATTACKS*/
playerAttaking.addEventListener('click', () => {
  /*Reducing the value*/
  monstersHealth.value = monstersHealth.value - randomNumberAttack();
  playerAttaking.setAttribute("disabled", "");
  monsterAttacking.removeAttribute("disabled", "");
  ballPlayer.style.display = "none";
  ballMonster.style.display = "flex"

  /*Condition to win*/
  if(monstersHealth.value === 0) {
    alert("PLAYER WINS");
  }
})


/* WHEN MONSTER ATTACKS */
monsterAttacking.addEventListener('click', () => {
  /*Reducing the value*/
  playersHealth.value = playersHealth.value - randomNumberAttack();
  monsterAttacking.setAttribute("disabled", "");
  playerAttaking.removeAttribute("disabled", "");
  ballPlayer.style.display = "flex";
  ballMonster.style.display = "none"
  /*Condition to win*/
  if(playersHealth.value === 0) {
    alert("Monster WINS");
  }

})


/* WHEN PLAYER HEALS */
healPlayer.addEventListener("click", () => {
  console.log("PLAYER IS HEALING!!")
})

/* WHEN MONSTER HEALS */
healMonster.addEventListener("click", () => {
  console.log("MONSTER IS HEALING!!")
})
console.log(healPlayer, healMonster)


//CONCLUSTION








/*
  STYLES GLOBALLY
*/
*,
*::after,
*::before {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

html {
  margin: 0px;
  padding: 0px;
  font-size:62.5%;
}

/*
  *
  * Project Styles
*/


/*The project background*/
.bg {
  background-color: #242424;
  height: 100vh;
  width: 100%;
}
/*container for the title*/
.container {
  height: 30vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  background-image: url('icons.jpg');
}

.title {
  color: #242424;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-weight: 800;
  font-size: 5rem;
  text-align: center;
  background-color: white;
  padding: 4.2rem;
}

/*
  Progress
*/

progress {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  height: 3rem;
  margin: 1rem 0rem;
  color: #ff0062;
}

progress[value]::-webkit-progress-value {
  background-color: #ff0062;
  transition: all 0.2s ease-out;
}

progress[value]::-moz-progress-bar {
  background-color: #ff0062;
  transition: all 0.2s ease-out;
}

button {
  font: inherit;
  background: beige;
  border: 1px solid beige;
  color:#242424;
  padding: 1rem 2rem;
  border-radius: 6px;
  cursor: pointer;
  margin: 1rem 0rem;
}

button:focus {
  outline: none;
}

button:hover,
button:active {
  background: #ff0062;
  border-color: #ff0062;
}



/*The cards part*/

.cards {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 60vh;
  width: 100%;
}

.player,.monster {
  display: flex;
  flex-direction: column;
  text-align: center;
  color: #fff;
  font-family: arial,sans-serif;
  font-size: 25px;
}

.ball-monster,
.ball-player {
  display: flex;
}

span {
  height: 25px;
  width: 25px;
  background-color: red;
  border: 1px solid red;
  border-radius: 100px;
  margin-left: 10px;
  display: none;
}




