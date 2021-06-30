# pigGame
Javascript dice game

This project was created by following the directions of a Udemy instructor. The project is a two-player dice game with a score limit to win.

Constructing this project has helped me to better practice and learn the following:
1) DOM manipulation
2) Creating functions
3) Ternary operator
4) Implementing logic

A breif overview of the functional JS is given below. A detailed flow chart exist in the code base as a PNG file. 

After creating the DOM elements the switchPlayer() function was constructed.
```JavaScript
const switchPlayer = function () {
  document.getElementById(`current--${activePlayer}`).textContent = 0;
  activePlayer = activePlayer === 0 ? 1 : 0; //switches to next player
  currentScore = 0;
  player0El.classList.toggle('player--active');
  player1El.classList.toggle('player--active');
};
```

Following this the functionality of the buttons was built in.
```JavaScript
btnRoll.addEventListener('click', function () {
  if (playing) {
    const dice = Math.trunc(Math.random() * 6) + 1;

    diceEl.classList.remove('hidden');
    diceEl.src = `dice-${dice}.png`; //Now when you click roll dice a dice will be displayed
    if (dice !== 1) {
      // currentScore = currentScore + dice;
      currentScore += dice;
      document.getElementById(
        `current--${activePlayer}`
      ).textContent = currentScore; //sets score of active player

      // current0El.textContent = currentScore; //Change later to display at current player not always player 1
    } else {
      switchPlayer();
    }
  }
});

btnHold.addEventListener('click', function () {
  if (playing) {
    scores[activePlayer] += currentScore;

    //scores[1] = scores[1] + currentScore;
    document.getElementById(`score--${activePlayer}`).textContent =
      scores[activePlayer];

    if (scores[activePlayer] >= 100) {
      playing = false;
      diceEl.classList.add('hidden');
      document
        .querySelector(`.player--${activePlayer}`)
        .classList.add('player--winner');
      document
        .querySelector(`.player--${activePlayer}`)
        .classList.remove('player--active');
    }
    ```
    
    The btnNew requires an initialization function to reset and restart the game, as shown.
    ```JavaScript
    const init = function () {
  scores = [0, 0]; //These are the scores that acumulate , not the current
  currentScore = 0;
  activePlayer = 0;
  playing = true;

  score1El.textContent = 0;
  score0El.textContent = 0;
  current0El.textContent = 0;
  current1El.textContent = 0;

  diceEl.classList.add('hidden');
  player0El.classList.remove('player--winner');
  player1El.classList.remove('player--winner');
  player0El.classList.add('player--active');
  player1El.classList.remove('player--active');
};
```

***End Walkthrough
