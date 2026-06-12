# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

- Says the inverese of the direction you need to go, such as if target 10, but you entered 1, it will say go lower.
- New game does not reset the game correctly upon game over.
- When starting a new and fresh game, Attempts are not aligned correctly, causing the score to not move upon first attempt.
- Difficulty does not seem to work, if you put in easy or hard, range does change to fit the correct range.
- History is not synced and not resetting

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
|in: 5  | GO HIGHER! hint   | GO LOWER! hint  | None
|trg: 64| shown             | shown           | 
|-------|-------------------|-----------------|------------------------|
|in: 100| GO LOWER! hint    | GO HIGHER! hint | None
|trg: 83| shown             | shown           | 
|-------|-------------------|-----------------|------------------------|
|Browser| Attempts: 8       | Attempts: 7     | None
|Restart|                   |                 | 
|-------|-------------------|-----------------|------------------------|
|in: 2  | Game contunes     | Game over       | None
|trg: 10|                   |                 |
|att: 2 |                   |                 | 
|-------|-------------------|-----------------|------------------------|
|Click  | Game restart,     | Does not allow  | None
|Restart| allows input      | any inputs      |
|game   |                   |                 |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

- I have used Claude as my primary tool for analysis and changing the code.
- Claude's suggestion correctly fixed the bug in which the game does not
sucessfully restart after game win or loose, in which the correct behavior was established. 
  *in this case, it suggested the following code snippet :
    if new_game:
      st.session_state.attempts = 0
      st.session_state.secret = random.randint(low, high)
      st.session_state.status = "playing"
      st.session_state.history = []
      st.success("New game started.")
      st.rerun()
  And I verified it worked by testing out the cases that did not worked before, (hitting new game after winning and loosing the game).
  *Suprisingly fixed 2 bugs I never knew existed, the issue where the difficulty range is not
  set and history is not resetting upon game restart.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
