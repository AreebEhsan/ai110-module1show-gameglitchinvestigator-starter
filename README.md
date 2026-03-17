# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- This project involved debugging and repairing an AI-generated Streamlit number guessing game. The goal was to analyze the behavior of the application, identify logical and state management bugs, and fix them while documenting how AI tools contributed to the debugging process.

- Several bugs were identified during the investigation. The game accepted invalid guesses outside the allowed range (for example negative numbers), the hint system sometimes gave incorrect guidance, and the session state initialization caused incorrect values for attempts, score, and history at startup. These issues made the game behave inconsistently and sometimes appear broken.

- To fix these problems, I corrected the session state initialization so that attempts start at zero and the game state resets properly when a new game begins. I added validation to reject guesses outside the allowed difficulty range and ensured that attempts are only consumed for valid guesses. I also refactored the guessing logic into `logic_utils.py` and corrected the hint logic so that guesses above the secret return "Too High" with a "Go LOWER" hint, and guesses below return "Too Low" with a "Go HIGHER" hint.

- The fixes were verified using both manual testing through the Streamlit interface and automated testing using pytest. The automated tests confirmed that correct guesses return a win, higher guesses return "Too High", and lower guesses return "Too Low".

- [ ] Describe the game's purpose.
- [ ] Detail which bugs you found.
- [ ] Explain what fixes you applied.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
