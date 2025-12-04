<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Days of the Week – Practice Games</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: "Comic Sans MS", "Baloo", system-ui, sans-serif;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(135deg, #ffefd5, #e0f7fa);
      color: #333;
    }

    header {
      text-align: center;
      padding: 20px 10px 10px;
    }

    h1 {
      margin: 0;
      font-size: 2.4rem;
      color: #2e7d32;
      text-shadow: 1px 1px 0 #fff;
    }

    .subtitle {
      margin-top: 8px;
      font-size: 1.1rem;
    }

    .container {
      max-width: 900px;
      margin: 0 auto 40px;
      padding: 0 15px 30px;
    }

    /* Menu */
    .game-menu {
      margin: 15px auto 30px;
      padding: 15px;
      border-radius: 12px;
      background: rgba(255, 255, 255, 0.9);
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    }

    .game-menu button {
      border: none;
      border-radius: 20px;
      padding: 8px 15px;
      font-size: 0.95rem;
      cursor: pointer;
      background: #ffb74d;
      transition: transform 0.1s, box-shadow 0.1s, background 0.2s;
    }

    .game-menu button:hover {
      transform: translateY(-1px);
      box-shadow: 0 3px 6px rgba(0,0,0,0.2);
      background: #ffa726;
    }

    /* Game cards */
    .game-section {
      margin-bottom: 30px;
      padding: 20px;
      border-radius: 16px;
      background: rgba(255, 255, 255, 0.95);
      box-shadow: 0 3px 8px rgba(0,0,0,0.18);
    }

    .game-section h2 {
      margin-top: 0;
      font-size: 1.5rem;
      color: #1565c0;
    }

    .game-description {
      margin-bottom: 15px;
      font-size: 0.98rem;
    }

    .back-top {
      margin-top: 15px;
      text-align: right;
    }

    .back-top a {
      text-decoration: none;
      font-size: 0.9rem;
      color: #1565c0;
    }

    .back-top a:hover {
      text-decoration: underline;
    }

    /* Buttons general */
    .btn {
      border: none;
      border-radius: 18px;
      padding: 8px 14px;
      font-size: 0.95rem;
      cursor: pointer;
      margin: 5px 4px;
      transition: transform 0.1s, box-shadow 0.1s, background 0.2s;
    }

    .btn-primary {
      background: #42a5f5;
      color: #fff;
    }

    .btn-primary:hover {
      background: #1e88e5;
      transform: translateY(-1px);
      box-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }

    .btn-secondary {
      background: #ab47bc;
      color: #fff;
    }

    .btn-secondary:hover {
      background: #8e24aa;
      transform: translateY(-1px);
      box-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }

    .btn-small {
      padding: 5px 10px;
      font-size: 0.85rem;
    }

    /* Feedback */
    .feedback {
      margin-top: 10px;
      min-height: 20px;
      font-weight: bold;
    }

    .correct {
      color: #2e7d32;
    }

    .incorrect {
      color: #c62828;
    }

    /* GAME 1 */
    #game1-question {
      font-size: 1.2rem;
      margin-bottom: 15px;
    }

    .g1-options {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 10px;
    }

    .g1-option-btn {
      background: #fff59d;
    }

    .g1-option-btn:hover {
      background: #fff176;
    }

    /* GAME 2 – order */
    .g2-list {
      list-style: none;
      padding: 0;
      margin: 10px 0 15px;
    }

    .g2-list li {
      background: #bbdefb;
      margin-bottom: 6px;
      padding: 8px 10px;
      border-radius: 10px;
      cursor: pointer;
      border: 2px solid transparent;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .g2-list li span.day-text {
      font-weight: bold;
    }

    .g2-list li.selected {
      border-color: #f9a825;
      background: #fff8e1;
    }

    .g2-list li.correct-order {
      border-color: #2e7d32;
    }

    .g2-list li.wrong-order {
      border-color: #c62828;
    }

    .small-hint {
      font-size: 0.85rem;
      color: #555;
    }

    /* GAME 3 – fill in the blanks */
    .g3-sentence {
      margin-bottom: 10px;
      padding: 8px;
      border-radius: 10px;
      background: #e1f5fe;
    }

    .g3-sentence span.label {
      display: block;
      margin-bottom: 3px;
      font-size: 0.9rem;
    }

    .g3-input {
      padding: 4px 6px;
      border-radius: 6px;
      border: 2px solid #90caf9;
      min-width: 120px;
      font-size: 0.95rem;
    }

    .g3-correct-answer {
      font-size: 0.85rem;
      margin-left: 6px;
    }

    /* GAME 4 – matching */
    .g4-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px 10px;
      align-items: center;
      margin-bottom: 10px;
    }

    .g4-grid div {
      font-size: 0.95rem;
    }

    .g4-select {
      width: 100%;
      padding: 4px 6px;
      border-radius: 8px;
      border: 2px solid #ce93d8;
      font-size: 0.95rem;
    }

    /* Responsive */
    @media (max-width: 600px) {
      .g4-grid {
        grid-template-columns: 1fr;
      }
      .g4-grid div {
        margin-bottom: 4px;
      }
    }
  </style>
</head>
<body>
  <a id="top"></a>
  <header>
    <h1>Days of the Week – Practice Games</h1>
    <p class="subtitle">Click a game below and practice the days of the week!</p>
  </header>

  <div class="container">
    <!-- Menu -->
    <nav class="game-menu">
      <button onclick="document.getElementById('game1').scrollIntoView()">Game 1 – Italian to English</button>
      <button onclick="document.getElementById('game2').scrollIntoView()">Game 2 – Put in Order</button>
      <button onclick="document.getElementById('game3').scrollIntoView()">Game 3 – Fill in the Blanks</button>
      <button onclick="document.getElementById('game4').scrollIntoView()">Game 4 – Match Translations</button>
    </nav>

    <!-- GAME 1 -->
    <section id="game1" class="game-section">
      <h2>Game 1 – Multiple Choice from Italian to English</h2>
      <p class="game-description">
        Guarda il giorno in italiano e clicca il giorno giusto in inglese. Practice the correct word and spelling!
      </p>

      <div id="game1-question"></div>
      <div class="g1-options" id="game1-options"></div>
      <div class="feedback" id="game1-feedback"></div>
      <button class="btn btn-primary" id="game1-next-btn">Next day ➜</button>

      <div class="back-top">
        <a href="#top">⬆ Back to top</a>
      </div>
    </section>

    <!-- GAME 2 -->
    <section id="game2" class="game-section">
      <h2>Game 2 – Put the Days in Order</h2>
      <p class="game-description">
        Click two days to swap their places. Put the days in the correct order from Monday to Sunday.
      </p>

      <p class="small-hint">Hint: Monday (Lunedì) is the first day, Sunday (Domenica) is the last. 😉</p>

      <ul class="g2-list" id="game2-list">
        <!-- Filled by JavaScript -->
      </ul>

      <button class="btn btn-primary" id="game2-check">Check order ✅</button>
      <button class="btn btn-secondary" id="game2-reset">Shuffle / Reset 🔁</button>
      <div class="feedback" id="game2-feedback"></div>

      <div class="back-top">
        <a href="#top">⬆ Back to top</a>
      </div>
    </section>

    <!-- GAME 3 -->
    <section id="game3" class="game-section">
      <h2>Game 3 – Fill in the Blanks (Spelling Practice)</h2>
      <p class="game-description">
        Write the correct day in each blank. Remember: start with a capital letter (Monday, Tuesday, ...).
      </p>

      <div id="game3-sentences">
        <div class="g3-sentence">
          <span class="label">1)</span>
          Today is Monday, tomorrow is
          <input class="g3-input" data-answer="Tuesday" />
          .
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">2)</span>
          Today is Thursday, yesterday was
          <input class="g3-input" data-answer="Wednesday" />
          .
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">3)</span>
          The day before Friday is
          <input class="g3-input" data-answer="Thursday" />
          .
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">4)</span>
          The day after Sunday is
          <input class="g3-input" data-answer="Monday" />
          .
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">5)</span>
          I play football on
          <input class="g3-input" data-answer="Saturday" />
          and
          <input class="g3-input" data-answer="Sunday" />
          .
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">6)</span>
          In Italy, <em>Mercoledì</em> is
          <input class="g3-input" data-answer="Wednesday" />
          in English.
          <span class="g3-correct-answer"></span>
        </div>

        <div class="g3-sentence">
          <span class="label">7)</span>
          I go to English class on
          <input class="g3-input" data-answer="Tuesday" />
          and
          <input class="g3-input" data-answer="Thursday" />
          .
          <span class="g3-correct-answer"></span>
        </div>
      </div>

      <button class="btn btn-primary" id="game3-check">Check answers ✅</button>
      <button class="btn btn-secondary btn-small" id="game3-clear">Clear all ✨</button>
      <div class="feedback" id="game3-feedback"></div>

      <div class="back-top">
        <a href="#top">⬆ Back to top</a>
      </div>
    </section>

    <!-- GAME 4 -->
    <section id="game4" class="game-section">
      <h2>Game 4 – Match English Day to Italian Translation</h2>
      <p class="game-description">
        Abbina ogni giorno inglese alla traduzione italiana corretta. Use the dropdown menus. 😊
      </p>

      <div class="g4-grid" id="game4-grid">
        <!-- Each row: English label + select -->
        <div>Monday</div>
        <div>
          <select class="g4-select" data-answer="Lunedì">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Tuesday</div>
        <div>
          <select class="g4-select" data-answer="Martedì">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Wednesday</div>
        <div>
          <select class="g4-select" data-answer="Mercoledì">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Thursday</div>
        <div>
          <select class="g4-select" data-answer="Giovedì">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Friday</div>
        <div>
          <select class="g4-select" data-answer="Venerdì">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Saturday</div>
        <div>
          <select class="g4-select" data-answer="Sabato">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>

        <div>Sunday</div>
        <div>
          <select class="g4-select" data-answer="Domenica">
            <option value="">-- choose --</option>
            <option value="Lunedì">Lunedì</option>
            <option value="Martedì">Martedì</option>
            <option value="Mercoledì">Mercoledì</option>
            <option value="Giovedì">Giovedì</option>
            <option value="Venerdì">Venerdì</option>
            <option value="Sabato">Sabato</option>
            <option value="Domenica">Domenica</option>
          </select>
        </div>
      </div>

      <button class="btn btn-primary" id="game4-check">Check matches ✅</button>
      <button class="btn btn-secondary btn-small" id="game4-reset">Reset choices 🔁</button>
      <div class="feedback" id="game4-feedback"></div>

      <div class="back-top">
        <a href="#top">⬆ Back to top</a>
      </div>
    </section>
  </div>

  <script>
    // ===== GENERAL DATA =====
    const daysEnglish = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
    const daysItalian = ["Lunedì", "Martedì", "Mercoledì", "Giovedì", "Venerdì", "Sabato", "Domenica"];

    // Small helper: shuffle an array (Fisher-Yates)
    function shuffleArray(array) {
      const arr = array.slice();
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    }

    // =========================
    // GAME 1 – Italian to English Multiple Choice
    // =========================
    (function setupGame1() {
      const questionEl = document.getElementById("game1-question");
      const optionsContainer = document.getElementById("game1-options");
      const feedbackEl = document.getElementById("game1-feedback");
      const nextBtn = document.getElementById("game1-next-btn");

      const dayPairs = daysEnglish.map((eng, index) => ({
        english: eng,
        italian: daysItalian[index]
      }));

      let currentCorrectAnswer = null;
      let allowClick = true;

      // Create a new question
      function newQuestion() {
        allowClick = true;
        feedbackEl.textContent = "";
        feedbackEl.className = "feedback";

        // pick a random pair
        const randomPair = dayPairs[Math.floor(Math.random() * dayPairs.length)];
        currentCorrectAnswer = randomPair.english;
        questionEl.innerHTML = `<strong>Italian:</strong> ${randomPair.italian} ➜ <span style="font-size:1.1rem;">?</span>`;

        // create options: correct + some incorrect ones
        const otherOptions = dayPairs
          .filter(p => p.english !== randomPair.english)
          .map(p => p.english);
        const numberOfOptions = 4;
        const randomOthers = shuffleArray(otherOptions).slice(0, numberOfOptions - 1);
        const options = shuffleArray([randomPair.english, ...randomOthers]);

        // render buttons
        optionsContainer.innerHTML = "";
        options.forEach(option => {
          const btn = document.createElement("button");
          btn.textContent = option;
          btn.className = "btn g1-option-btn";
          btn.addEventListener("click", () => {
            if (!allowClick) return;
            if (option === currentCorrectAnswer) {
              feedbackEl.textContent = "Correct! 😊";
              feedbackEl.className = "feedback correct";
              allowClick = false;
            } else {
              feedbackEl.textContent = "Try again! 😅";
              feedbackEl.className = "feedback incorrect";
            }
          });
          optionsContainer.appendChild(btn);
        });
      }

      nextBtn.addEventListener("click", newQuestion);

      // Initialize first question
      newQuestion();
    })();


    // =========================
    // GAME 2 – Put the Days in Order
    // =========================
    (function setupGame2() {
      const listEl = document.getElementById("game2-list");
      const checkBtn = document.getElementById("game2-check");
      const resetBtn = document.getElementById("game2-reset");
      const feedbackEl = document.getElementById("game2-feedback");

      let selectedIndex = null;

      // Build shuffled list
      function buildList() {
        listEl.innerHTML = "";
        feedbackEl.textContent = "";
        feedbackEl.className = "feedback";

        const shuffled = shuffleArray(daysEnglish);
        shuffled.forEach(day => {
          const li = document.createElement("li");
          const span = document.createElement("span");
          span.textContent = day;
          span.className = "day-text";
          li.appendChild(span);
          li.dataset.day = day;

          li.addEventListener("click", () => handleSelect(li));
          listEl.appendChild(li);
        });
      }

      function handleSelect(li) {
        const items = Array.from(listEl.children);

        // remove order classes
        items.forEach(item => {
          item.classList.remove("correct-order", "wrong-order");
        });

        const index = items.indexOf(li);
        if (selectedIndex === null) {
          selectedIndex = index;
          li.classList.add("selected");
        } else if (selectedIndex === index) {
          // click same again to unselect
          li.classList.remove("selected");
          selectedIndex = null;
        } else {
          // second click: swap
          const firstLi = items[selectedIndex];
          const secondLi = li;

          // swap data-day and text
          const tempDay = firstLi.dataset.day;
          firstLi.dataset.day = secondLi.dataset.day;
          secondLi.dataset.day = tempDay;

          const firstText = firstLi.querySelector(".day-text").textContent;
          firstLi.querySelector(".day-text").textContent = secondLi.querySelector(".day-text").textContent;
          secondLi.querySelector(".day-text").textContent = firstText;

          // clear selection
          firstLi.classList.remove("selected");
          selectedIndex = null;
        }
      }

      checkBtn.addEventListener("click", () => {
        const items = Array.from(listEl.children);
        let allCorrect = true;
        items.forEach((item, index) => {
          item.classList.remove("correct-order", "wrong-order", "selected");
          if (item.dataset.day === daysEnglish[index]) {
            item.classList.add("correct-order");
          } else {
            item.classList.add("wrong-order");
            allCorrect = false;
          }
        });

        if (allCorrect) {
          feedbackEl.textContent = "Perfect order! 🎉 Great job!";
          feedbackEl.className = "feedback correct";
        } else {
          feedbackEl.textContent = "Not yet, try again! 🔁";
          feedbackEl.className = "feedback incorrect";
        }

        selectedIndex = null;
      });

      resetBtn.addEventListener("click", buildList);

      // Initialize
      buildList();
    })();


    // =========================
    // GAME 3 – Fill in the Blanks
    // =========================
    (function setupGame3() {
      const inputs = document.querySelectorAll(".g3-input");
      const checkBtn = document.getElementById("game3-check");
      const clearBtn = document.getElementById("game3-clear");
      const feedbackEl = document.getElementById("game3-feedback");

      function normalizeAnswer(text) {
        return text.trim();
      }

      checkBtn.addEventListener("click", () => {
        let correctCount = 0;
        let total = inputs.length;

        inputs.forEach(input => {
          const correct = input.dataset.answer;
          const user = normalizeAnswer(input.value);
          const parentSentence = input.parentElement;
          const answerSpan = parentSentence.querySelector(".g3-correct-answer");

          if (user.toLowerCase() === correct.toLowerCase()) {
            input.style.borderColor = "#2e7d32";
            input.style.backgroundColor = "#c8e6c9";
            answerSpan.textContent = "";
            correctCount++;
          } else {
            input.style.borderColor = "#c62828";
            input.style.backgroundColor = "#ffcdd2";
            answerSpan.textContent = `Correct: ${correct}`;
            answerSpan.style.color = "#c62828";
          }
        });

        if (correctCount === total) {
          feedbackEl.textContent = "All answers correct! 🎉 Excellent!";
          feedbackEl.className = "feedback correct";
        } else {
          feedbackEl.textContent = `You got ${correctCount} of ${total} correct. Keep trying! 💪`;
          feedbackEl.className = "feedback incorrect";
        }
      });

      clearBtn.addEventListener("click", () => {
        inputs.forEach(input => {
          input.value = "";
          input.style.borderColor = "#90caf9";
          input.style.backgroundColor = "#ffffff";
          const parentSentence = input.parentElement;
          const answerSpan = parentSentence.querySelector(".g3-correct-answer");
          if (answerSpan) {
            answerSpan.textContent = "";
          }
        });
        feedbackEl.textContent = "";
        feedbackEl.className = "feedback";
      });
    })();


    // =========================
    // GAME 4 – Match English to Italian
    // =========================
    (function setupGame4() {
      const selects = document.querySelectorAll(".g4-select");
      const checkBtn = document.getElementById("game4-check");
      const resetBtn = document.getElementById("game4-reset");
      const feedbackEl = document.getElementById("game4-feedback");

      checkBtn.addEventListener("click", () => {
        let correctCount = 0;
        const total = selects.length;

        selects.forEach(select => {
          const correct = select.dataset.answer;
          const chosen = select.value;
          if (chosen === correct) {
            select.style.borderColor = "#2e7d32";
            select.style.backgroundColor = "#c8e6c9";
            correctCount++;
          } else {
            select.style.borderColor = "#c62828";
            select.style.backgroundColor = "#ffcdd2";
          }
        });

        if (correctCount === total) {
          feedbackEl.textContent = "All 7 are correct! 🎉 Bravissimo/a!";
          feedbackEl.className = "feedback correct";
        } else {
          feedbackEl.textContent = `You matched ${correctCount} of ${total}. Try again! 😊`;
          feedbackEl.className = "feedback incorrect";
        }
      });

      resetBtn.addEventListener("click", () => {
        selects.forEach(select => {
          select.value = "";
          select.style.borderColor = "#ce93d8";
          select.style.backgroundColor = "#ffffff";
        });
        feedbackEl.textContent = "";
        feedbackEl.className = "feedback";
      });
    })();
  </script>
</body>
</html>
