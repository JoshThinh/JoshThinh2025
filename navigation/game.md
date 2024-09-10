---
layout: game
title: Game
permalink: /game/
---

# Passcode Puzzle Game

<div id="game-container">
  <h2>Enter a Passcode to Start the Game</h2>
  <input type="text" id="initial-passcode" placeholder="Enter a random passcode">
  <button id="start-game-btn">Start Game</button>
  <button id="reset-game-btn" style="display:none;">Reset Game</button>

  <div id="timer-container" style="display: none;">
    <h3>Time Left: <span id="countdown-timer">60</span> seconds</h3>
    <p>Solve the puzzle below:</p>
    <div id="puzzle">
      <p>What is 5 + 3?</p>
      <input type="text" id="puzzle-answer" placeholder="Enter your answer">
      <button id="submit-answer-btn">Submit Answer</button>
    </div>

    <div id="reveal-passcode" style="display: none;">
      <h4>Congratulations! The correct passcode is: <span id="revealed-passcode"></span></h4>
      <input type="text" id="final-passcode" placeholder="Enter the revealed passcode">
      <button id="stop-timer-btn">Submit Final Passcode</button>
    </div>
  </div>

  <h3 id="message"></h3>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    let timer;
    let timeLeft = 60;
    let userPasscode = "";

    // Start game button
    document.getElementById('start-game-btn').addEventListener('click', function() {
      userPasscode = document.getElementById('initial-passcode').value;
      if(userPasscode === "") {
        document.getElementById('message').innerText = "Please enter a passcode.";
        return;
      }

      // Hide the passcode input and start button
      document.getElementById('initial-passcode').style.display = "none";
      document.getElementById('start-game-btn').style.display = "none";

      // Show the reset button
      document.getElementById('reset-game-btn').style.display = "inline-block";

      // Display timer and start countdown
      document.getElementById('timer-container').style.display = "block";
      startCountdown();
    });

    // Timer logic
    function startCountdown() {
      clearInterval(timer); // Clear any existing timers
      timeLeft = 60; // Reset timeLeft to 60
      document.getElementById('countdown-timer').innerText = timeLeft; // Initialize the timer display

      timer = setInterval(function() {
        if (timeLeft > 0) {
          timeLeft--;
          document.getElementById('countdown-timer').innerText = timeLeft; // Update the countdown display
        } else {
          clearInterval(timer);
          document.getElementById('message').innerText = "Time's up! Please restart the game.";
          document.getElementById('timer-container').style.display = "none";
        }
      }, 1000);
    }

    // Puzzle submit logic
    document.getElementById('submit-answer-btn').addEventListener('click', function() {
      const answer = document.getElementById('puzzle-answer').value;
      if(answer == "8") {
        document.getElementById('reveal-passcode').style.display = "block";
        document.getElementById('revealed-passcode').innerText = userPasscode;
      } else {
        document.getElementById('message').innerText = "Incorrect answer. Try again!";
      }
    });

    // Stop timer logic
    document.getElementById('stop-timer-btn').addEventListener('click', function() {
      const finalPasscode = document.getElementById('final-passcode').value;
      if(finalPasscode === userPasscode) {
        clearInterval(timer);
        document.getElementById('message').innerText = "You have successfully stopped the timer!";
      } else {
        document.getElementById('message').innerText = "Incorrect passcode. Try again!";
      }
    });

    // Reset game logic
    document.getElementById('reset-game-btn').addEventListener('click', function() {
      clearInterval(timer); // Stop the timer
      timeLeft = 60; // Reset timeLeft to 60

      // Reset all fields and hide elements
      document.getElementById('initial-passcode').value = "";
      document.getElementById('initial-passcode').style.display = "inline-block";
      document.getElementById('start-game-btn').style.display = "inline-block";
      document.getElementById('timer-container').style.display = "none";
      document.getElementById('reveal-passcode').style.display = "none";
      document.getElementById('reset-game-btn').style.display = "none";
      document.getElementById('message').innerText = "";
      document.getElementById('puzzle-answer').value = "";
      document.getElementById('final-passcode').value = "";
      document.getElementById('countdown-timer').innerText = "60"; // Reset timer display
    });
  });
</script>

<style>
  #game-container {
    text-align: center;
    margin-top: 20px;
  }

  #puzzle {
    margin-top: 20px;
  }

  #reveal-passcode {
    margin-top: 20px;
  }

  input {
    margin: 10px;
    padding: 5px;
  }

  button {
    padding: 7px 15px;
    cursor: pointer;
  }
</style>
