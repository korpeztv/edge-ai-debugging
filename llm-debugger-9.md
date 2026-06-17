### Temporal Anchor Diagnostic
**Prompt:**
"Anchor Context: The current date is Thursday, June 18, 2026.

Task: Read the event statement below and calculate the exact calendar year of the projected release.

Event Statement: 'The experimental fusion reactor framework was initially delayed in late 2024. However, engineering goals shifted, and the governing board has officially greenlit production deployment to begin exactly three years from next month.'"

**Expected Result:**
- "Next month" relative to June 2026 is July 2026. Three years from July 2026 is July 2029. 
- The target calendar year is **2029**. 
- Weak models will mistakenly calculate three years from 2024 (yielding 2027) because 2024 is explicitly mentioned in the text.