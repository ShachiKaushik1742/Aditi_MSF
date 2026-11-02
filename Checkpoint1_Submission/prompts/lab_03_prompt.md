# Reconstructed Lab 03 prompt

This prompt uses short, direct instructions. It uses Purdue GenAI Studio with the official OpenAI Python SDK. GenAI Studio provides an OpenAI-compatible chat-completions API.

```text
Add the four roles from Figure 1 of Francis and Zhang (2026) to the seven-step Python desk in this folder. Use the official OpenAI Python SDK with Purdue GenAI Studio's OpenAI-compatible API.

Read API_KEY and MODEL from the .env file in this folder. Use this API base URL: https://genai.rcac.purdue.edu/api. Pass API_KEY to the SDK. Use MODEL as the model ID. Do not print or save the key. Do not put a company name or ticker in the code.

Keep the existing seven data steps. Use their saved filings, facts, ratios, quarterly figures, and peer figures as inputs to the roles.

Make one model call for each role. Give each role its own instructions. Each role shall receive only the information that the Strategy Manager sends it. Send each role one JSON object with these fields:
- task
- context
- expected_output

The roles shall work as follows.

1. Research Analyst

- Describe the company's business model, competitive position, catalysts, and recent developments.
- Use only the 10-K's Business and Management's Discussion and Analysis (MD&A) sections, and the earnings release.
- The Strategy Manager shall send the relevant source text. Preserve line numbers from the saved plain-text filings.
- Quote the source line for every claim. Include the source filename and filing accession with each quote.

2. Financial Analyst

- Use the facts from Step 4, the ratios from Step 5, the quarter from Step 6, and the peers from Step 7.
- Give the filing and the statement line, or the XBRL tag and period, for every number.
- Show the arithmetic for every ratio.
- State the definition used wherever a filing offers two definitions. Use these definitions: revenue growth is latest fiscal-year revenue divided by prior-year revenue, minus one; operating margin is operating income divided by total revenue; return on average equity is net income divided by average beginning and ending stockholders' equity; debt to equity is long-term debt, including its current portion, divided by stockholders' equity; free cash flow is cash from operations minus additions to property and equipment; P/E is the share price divided by GAAP diluted EPS.
- The Analyst may ask the code calculator to calculate more ratios. The Analyst shall not calculate or estimate a number in the model.

3. Investment Advisor

- Use only the Research Analyst's and Financial Analyst's outputs. Do not use other information.
- Give a thesis and one recommendation: Buy, Hold, or Sell.
- Name the one number that decides the recommendation. Give its source and explain the reason for the decision.

4. Strategy Manager

- Create and send the JSON tasks to the other roles.
- Check that the final report has all five parts, and that the parts are consistent:
  1. Overview
  2. Market Positioning and Growth Outlook
  3. Valuation Insights
  4. Future Developments and Strategic Recommendations
  5. Investment Recommendation
- If a part is missing or inconsistent, send that part back to its role once. Include the specific problem in the new task. Do not request a second revision.
- Compile the five parts into one Markdown report. If a part still fails after its one revision, state the problem. Do not invent facts or numbers.

Print each role's name when it runs. Save the report as Markdown in the current run's output folder. On the first line, name every filing read and give its accession number. On the second line, give the run date and time. Print the saved report path.

Use the official SDK's documented setup. Tell me the exact command to install any required package. Tell me the exact command to run the app with a ticker, peers, and a price. Accept an optional --price-date and --price-source so the report can identify the price used. Use this command shape:

python desk_app.py <TICKER> --peers <PEER_1,PEER_2> --price <PRICE> --price-date <YYYY-MM-DD> --price-source <SOURCE>
```
