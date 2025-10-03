---
toc: False
layout: post
data: web-dev
title:  Eshika's Blog (9/21/2025)
description: MY personal blog
categories: ['GitHub Pages']
permalink: /web-dev/blog_eshika
breadcrumb: True
---

| Hack Objective             | Example Evidence                                                     | Reflection Question                                                                                                                                                                                                                              | Rank (0–5) |
| -------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- |
| Tools & Equipment          | Screenshots of VSCode setup, GitHub connection, Makefile running     | How did I learn or improve my tool workflow this week?  <br> ![tools]({{site.baseurl}}/images/webdev/image.png)                                                                                                                                                        | 4          |
| Portfolio & Blogging       | Blog posts showing challenges and solutions                          | How did I improve in LxD this week?  <br> ![tools]({{site.baseurl}}/images/webdev/image-1.png)                                                                                                                                                                               | 3          |
| Theme, Style, Layout       | Before/after site design changes                                     | What design choices did I make, and why? <br> I made changes to the original Rock-Paper-Scissors lesson page. I worked on formatting and structuring the lesson plan. I also experimented with implementing and explaining OOP in a clearer way. | 4          |
| JavaScript Frontend Basics | Code snippets, commit history, working UI components                 | How did I apply Markdown, HTML, or JavaScript to improve presentation or interactivity? <br> I added interactive buttons and formatted sections with Markdown. Small JavaScript tweaks improved user experience.                                 | 3          |
| AI Evidence in Work        | Prompts and AI output with your improvements                         | Where did AI help, and where did I override or improve on AI response? <br> AI helped brainstorm initial explanations, but I rewrote them to fit my voice and expanded with examples.                                                            | 4          |
| Manifesto Evidence         | Peer review logs, joint commits, screenshots of collaborative coding | How did working with others impact my approach or give me insight into better LxD? <br> Collaborating gave me perspective on simplifying explanations for learners. Team feedback made me rethink clarity.                                       | 5          |
| Learning Through Mistakes  | Bug logs, fix notes, before/after comparisons                        | What mistake taught me the most this week? <br> I initially broke my CSS styling by misplacing a bracket. Debugging taught me to slow down, check syntax, and rely on commit history.                                                            | 3          |


<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>CSA Java Learning Goals</title>
  <style>
    
    button {
      background-color: #4cafaaff;
      color: white;
      padding: 12px 20px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-bottom: 20px;
    }
    button:hover {
      background-color: #a04598ff;
    }
    #java-topics {
      display: none;
      text-align: left;
      max-width: 400px;
      margin: 0 auto;
      background: #931a1aff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>

  <h1>CSA Java Learning Goals</h1>
  <button onclick="revealTopics()">Show What I Want to Learn</button>

  <div id="java-topics">
    <h2>Java Topics:</h2>
    <ul>
      <li>Java syntax and basic structure</li>
      <li>Data types and variables</li>
      <li>Control structures (if, loops, switch)</li>
      <li>Methods and parameter passing</li>
      <li>Object-Oriented Programming (classes, objects, inheritance, polymorphism)</li>
      <li>Arrays and ArrayLists</li>
      <li>Recursion</li>
      <li>AP CSA free response style practice</li>
    </ul>
  </div>

  <script>
    function revealTopics() {
      let topics = document.getElementById("java-topics");
      if (topics.style.display === "none") {
        topics.style.display = "block";
      } else {
        topics.style.display = "none";
      }
    }
  </script>

</body>
</html>


<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cat Zoom & Gopher Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 20px;
    }

    /* Cat animation */
    .cat {
      position: absolute;
      top: 50px;
      left: -200px;
      width: 150px;
      transition: transform 2s linear;
    }

    .zoom {
      transform: translateX(120vw);
    }

    /* Gopher game */
    #game {
      margin-top: 150px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-gap: 10px;
      justify-content: center;
      margin: 20px 0;
    }

    .square {
      width: 100px;
      height: 100px;
      background: #eee;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      border-radius: 8px;
      font-size: 24px;
      font-weight: bold;
      color: #444;
    }

    .square.revealed {
      background: #ffeb3b;
    }

    #status {
      font-size: 18px;
      margin-top: 10px;
    }

    #score {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>🐱 Cat Zoom & Guess the Gopher 🐹</h1>

  <!-- Cat -->
  <img src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif" class="cat" id="cat">

  <button onclick="zoomCat()">Zoom Cat!</button>

  <!-- Gopher game -->
  <div id="game">
    <h2>Find the Gopher!</h2>
    <p>You have <span id="tries">3</span> tries.</p>
    <div class="grid" id="grid"></div>
    <p id="status"></p>
    <p>Score: <span id="score">0</span></p>
    <button onclick="resetGame()">New Round</button>
  </div>

  <script>
    // === Cat Zoom ===
    function zoomCat() {
      const cat = document.getElementById('cat');
      cat.classList.remove('zoom');
      void cat.offsetWidth; // restart animation trick
      cat.classList.add('zoom');
    }

    // === Gopher Game ===
    const grid = document.getElementById("grid");
    let gopherIndex, tries, score = 0;

    function createGrid() {
      grid.innerHTML = "";
      for (let i = 0; i < 9; i++) {
        const square = document.createElement("div");
        square.classList.add("square");
        square.dataset.index = i;
        square.addEventListener("click", guessSquare);
        grid.appendChild(square);
      }
    }

    function resetGame() {
      tries = 3;
      gopherIndex = Math.floor(Math.random() * 9);
      document.getElementById("tries").textContent = tries;
      document.getElementById("status").textContent = "";
      createGrid();
    }

    function guessSquare(e) {
      if (tries <= 0) return;
      const square = e.target;
      const index = parseInt(square.dataset.index);

      if (index === gopherIndex) {
        square.textContent = "🐹";
        document.getElementById("status").textContent = "You found the gopher!";
        score++;
        document.getElementById("score").textContent = score;
        tries = 0;
      } else {
        square.textContent = "❌";
        square.classList.add("revealed");
        tries--;
        document.getElementById("tries").textContent = tries;
        if (tries === 0) {
          document.getElementById("status").textContent = "No tries left! The gopher was here.";
          const answer = document.querySelector(`.square[data-index='${gopherIndex}']`);
          answer.textContent = "🐹";
        }
      }
    }

    // Initialize
    resetGame();
  </script>
</body>
</html>




