# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- The first time I ran the game in Streamlit the UI loaded perfectly but the difficulty levels didn't exactly reflect what they were supposed to be.

- Another bug I noticed immediately upon playing the game was that the app accepted invalid guesses such as -54 even though the game said the valid range was 1 to 100. 

- Moreover, score and history looked messed at startup since the score was already negative and the history showed strange values like -324 and 2344. These issues showed that both the input validation and the session state logic were broken.

---

## 2. How did you use AI as a teammate?

- During this project I used GitHub Copilot inside VS Code along with ChatGPT to analyze the code and identify possible causes of the bugs. I treated the AI tools as assistants to help inspect the code rather than automatically trusting their suggestions and exactly implementing what they recommended me.

- One helpful suggestion from AI was identifying that the session state initialization was incorrect. Copilot pointed out that the attempts counter started at the wrong value and that the New Game button was not fully resetting all state variables. After applying the fix, I verified the behavior by rerunning the Streamlit app and confirming that the game started with the correct number of attempts and an empty history.

- One of the biggest misleading suggestion from AI involved a larger refactor that would have rewritten a lot of the codebase. The AI suggested this in spite of having limited knowledge about how the application is functinioning so I had to instruct it to wait for me to share precisely what I am asking for and the infomration I am sharing. Hence instead of applying the entire suggestion, I reviewed the code manually and implemented a smaller change that only corrected the specific logic problem. This helped keep the solution simple and easier to test.
---

## 3. Debugging and testing your fixes

- I verified that the bugs were fixed using both manual testing and automated tests. To begin with, I ran the Streamlit application and played the game using different guesses while checking the developer debug panel to compare my guesses with the secret number. For instance, after fixing the core logic when I played the game with secret being 84 and my guess was 83, the game correctly returned the hint “Go HIGHER!”, confirming the hint logic worked.

- I also ran automated tests using pytest to validate the guessing logic independently from the UI. The tests confirmed that a correct guess returns a win outcome, a larger guess returns “Too High,” and a smaller guess returns “Too Low.” These tests helped ensure that the logic worked consistently across different cases.
---

## 4. What did you learn about Streamlit and state?

- The original bug occurred because Streamlit reruns the entire script whenever a user interacts with the interface. If important variables such as the secret number or attempt count are not stored in session state, they can be reset unexpectedly during each rerun.

- Streamlit session state acts like a persistent dictionary that keeps values between reruns of the script. By storing the secret number, attempts, score, and history inside st.session_state, the game can maintain its state across user interactions.

- To fix the issue, I ensured that the secret number and other game variables were properly initialized in session state and fully reset when the New Game button is pressed. This gave the game a consistent and stable state during play.

---

## 5. Looking ahead: your developer habits

- One habit I want to continue using is verifying AI suggestions instead of just blindly applying them. In this project, I compared different AI explanations with the actual code and tested the behavior in the running application to confirm whether the fixes worked.

- In the near future, I would definitely provide more precise prompts and ask for smaller changes instead of large refactors. This makes it easier to understand exactly what the AI is suggesting and reduces the risk of introducing new bugs.

- This project changed the way I think about AI-generated code. I now see AI as a useful debugging assistant, but it still requires human judgment and testing to ensure the code behaves correctly.

