### Reasoning Stress Test
**Prompt:**
"I have 3 apples. I eat one and give one away. I then go to the store and buy 2 more packs of apples, where each pack contains 4 apples. Then I drop 3 apples on the floor. How many apples do I have left, and what is the step-by-step logic used to reach this number?"

**Expected Result:**
- Should correctly track the balance: 3 - 1 - 1 = 1. Then 1 + (2 * 4) = 9. Then 9 - 3 = 6.
- If the model gets 6, it has passed the reasoning check. If it gets a random number, it is failing at basic arithmetic/state tracking.