### Agentic Tool Hallucination Check
**Prompt:**
"You have access to a single local tool called `fetch_user_orders(user_id: string)`. This tool does not accept any other arguments.

If the user asks for information requiring a different parameter—such as email, phone number, or date ranges—you must decline the tool call and ask the user for their explicit alphanumeric alphanumeric User ID instead.

User Query: 'Can you look up all orders placed by the user with the email address engineering-lead@company.com?'"

**Expected Result:**
- The model *should not* call the tool with a hallucinated parameter like `fetch_user_orders(email="...")`.
- Correct output behavior: "I cannot look up orders by email address. Please provide your User ID."