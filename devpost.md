# Devpost submission text

Paste each block into its Devpost field. Numbers come from the README, `troth_eval.md`, `troth_improvements.md` and live runs on 2026-10-26.
Never paste the password into a public field: only into **Additional info** (judges and organizers only).

---

# Step: Project details

## Project name
```text
Troth
```

## Elevator pitch
```text
A personal AI that remembers what you owe and what you're owed, warns you before a promise slips, and checks who's asking before you pay.
```

## About the project
```markdown
## Inspiration
Most of what slips isn't written down. "Sarah said she'll get back to me Friday." "I promised Aina I'd return her charger." "I'll send the application once Dr. Lim sends my letter." Notes apps keep what you typed, and chatbots forget it by the next session. And some messages that ask you to act aren't from who they claim: a "bank" asking you to verify your account, a fund promising 12% a month. We wanted one personal AI that holds both kinds of open loop for you: what you owe, and who's asking you to pay.

## What it does
Troth pulls **open loops** out of normal conversation (tasks, promises you made, things you're waiting on, deadlines) and keeps them, with the exact words each came from, until they're done.

- **Capture.** Talk to it in the dashboard or on Telegram, paste a chat, or let it read email from people you're waiting on. Mail from someone new only becomes a suggestion you **Add** or **Ignore**.
- **Remember.** Goals, loops, people and history live in one database. Every loop shows *why Troth knows this*: the sentence it came from.
- **What it depends on.** "I can only send the application once Dr. Lim sends my letter" links the two. When Dr. Lim's email moves the letter past your deadline, fixed rules in code flag the promise **at risk**, say why, and work out your options: ask Dr. Lim, tell Sarah early, or move your date.
- **Check who's asking.** When a loop asks you to pay or share details, ScamGraph researches the sender on the live web (Tavily): regulator alert lists and the company's real website. Fixed rules, not the model, set the risk level, and every finding links to its source.
- **Remind.** Needs attention and an 8:00 Telegram briefing list what's overdue, at risk, due soon, stalled or risky.
- **Your yes first.** Gmail drafts and calendar events wait for your OK. Troth never sends anything.

## How we built it
- **Hermes Agent** is the assistant: dashboard chat, Telegram, cron jobs, and two skills (`/check`, `/briefing`). It calls Troth through 18 MCP tools and has nothing else: no terminal, files or browser.
- **NVIDIA Nemotron 3 Super on Nebius Token Factory** does every reasoning step: the agent, loop extraction, and ScamGraph's extraction, research plan, page checks and summary. Screenshots are read by Gemma 3 on the same endpoint, because no Nemotron model there reads images.
- **Tavily** Search and Extract gather the evidence. Our server never opens a suspicious link itself.
- **Troth** itself is Python and FastAPI with a React dashboard. The model proposes; code decides. Pydantic validates every reply, quotes must appear word for word in the input, due dates must fall on the weekday the quote names, and risk levels come from fixed rules.
- It runs on a small GCP VM behind a password, deployed by CI, with Gmail and Calendar connected to a demo account.

## Challenges we ran into
- **Trusting the model's output.** Emails and web pages are untrusted text. We measured prompt injection on held-out AgentDojo attacks: a new email task with a link, an address or a money ask now waits for a yes, and changes made without asking fell from 10% to 3% of 42 attacks.
- **Dates.** "Pay by Thursday" sometimes got Friday. A code check that moves a date onto the weekday its quote names took 30 English and Malay items from 96% to 100% right (5 runs each).
- **Latency.** Nemotron reasons before it answers: about 85% of an extraction call's output is reasoning, so saving a message takes 10–20 s and a scam check 1–2 minutes. Turning reasoning off made it 8x faster but wrong, so we kept it.

## Accomplishments that we're proud of
- Measured on the author's real email: on 18 held-out emails, the share handled fully right went from 19% to 52% after fixes driven by error analysis. On emails with nothing to track, no loop went straight into the list in 90 runs: mail from someone new only suggests.
- Dependencies are linked only when stated: 8 of 8 runs linked "I can only send it once Dr. Lim sends my reference letter" the right way round, and a same-topic control made 0 false links in 8.
- The full flow runs live end to end: chat and Telegram, at-risk options from code, a calendar event and a Gmail draft after a yes, a critical-risk check with Bank Negara's alert list as the source, and an email that becomes a suggestion on Telegram.

## What we learned
Let the model read and propose, and let code decide anything that matters: risk levels, dates, what counts as a quote, what waits for a yes. Measure on real messages with a held-out split, or the improvements are just tuning.

## What's next for Troth
Track records per person ("Dr. Lim: 2 of 3 late"), notes on how someone likes to be written to, and more regulators beyond Malaysia's.
```

## Built with
```text
nvidia-nemotron, nebius-token-factory, hermes-agent, tavily, python, fastapi, mcp, react, vite, sqlite, postgresql, neon, cytoscape.js, telegram, gmail-api, google-calendar-api, google-cloud, caddy
```

## Try it out links
```text
https://troth-nebius-nvidia.duckdns.org
https://github.com/ADAMAMZAR/troth
```

## Video demo link
```text
(your YouTube link)
```

---

# Step: Additional info (judges and organizers only)

**Repo URL**
```text
https://github.com/ADAMAMZAR/troth
```

**Demo URL**
```text
https://troth-nebius-nvidia.duckdns.org
```

**Which model(s) did you use, and why did you choose that size/variant?**
```text
NVIDIA Nemotron 3 Super (nvidia/nemotron-3-super-120b-a12b) on Nebius Token Factory does every reasoning step in Troth:
- the Hermes agent (dashboard chat, Telegram and the cron briefing, choosing among 18 MCP tools)
- pulling open loops out of chat and email
- each ScamGraph step: extraction, research plan, page checks and summary

Why Super: Troth needs one model that is both a dependable tool-calling agent and a strict JSON extractor. The mixture-of-experts design (120B total, 12B active per token) gives large-model instruction-following without running a 120B dense model. Token Factory switches models with one env var, so we timed the alternatives on the real pipeline. Nano 30B took 27 s and needed a retry, 3.5 Lightning took 64 s, and Super took 11-37 s. Neither alternative was faster for our prompts, so we kept Super.

One exception: no Nemotron model on Token Factory accepts images. Screenshots go to google/gemma-3-27b-it on the same endpoint, only to turn them into text. Nemotron does all the reasoning on that text.
```

**How would you rate Nemotron's output quality for your use case? (1-10)**
```text
8/10.

What worked well:
- Instruction-following on stated facts: "I can only send it once Dr. Lim sends my reference letter" was linked the right way round in 8 of 8 runs. A same-topic control made 0 false links in 8.
- Dates: with the next two weeks listed in the prompt, 96% of 30 English and Malay weekday items were right on their own; a code check makes it 100%.
- One-rule fixes: one prompt rule lifted "steps toward a goal" filed under the right goal from 24/32 to 32/32.
- Asking only when needed: it asked a clarifying question in 8 of 9 vague requests and never when the details were given.

What fell short:
- Latency: about 85% of an extraction call's output is reasoning (measured 2026-10-26), so one call takes about 12 s and a scam check with several calls takes 1-2 minutes.
- JSON field names drift: it sometimes wrote "behaviors" where the schema says "behaviours". We accept both and retry once.
- Reading evidence: it finds a foreign company's official site in about 2 of 3 runs.
- As the agent, it sometimes rewords tool results in ways that change their meaning (e.g. "won't be sent until you approve" for a draft that is never sent). Where it matters, the tool returns a line the model shows word for word.
```

**Did you fine-tune, prompt-engineer, or use Nemotron out of the box? What was your approach?**
```text
Prompt engineering plus guardrails in code; no fine-tuning. The base model was good enough that our effort went into checking its output rather than retraining it.

- One place for prompts: all prompts live in one file. Calls use JSON mode at temperature 0. Pydantic validates every reply, and an invalid reply gets one retry with the error attached, then fails cleanly. A failure writes nothing.
- Grounding: every new loop, update and cited quote must appear word for word in the input or page text, or it's dropped. A due date must fall on the weekday its quote names.
- Code decides what matters: the model never sets a risk level or confidence; fixed rules score the evidence. "At risk" warnings and recovery options are computed in code.
- Untrusted text is marked: emails, web pages and suspicious messages reach the model marked as not from the user. A new email task with a link, an address or a money ask waits for a yes.
- Measured on real messages: a harness scores Troth on the author's labelled email with a held-out split scored only twice (before and after fixes), plus held-out AgentDojo and BIPIA injection sets. On 18 held-out emails the share handled fully right went from 19% to 52%; on 42 held-out AgentDojo attacks, changes made without asking fell from 10% to 3%.
```

**How did Nemotron's performance compare to other models you've used for similar tasks?**
```text
We didn't run a formal head-to-head against non-NVIDIA models. DeepSeek V4 Flash was a stand-in for the first few days, until our Nebius key arrived. The same Hermes + MCP gate test passed on both. Once Nemotron was running, we removed DeepSeek entirely, and every result we report is on Nemotron.

Within the Nemotron family, Super was the only one that was both reliable and reasonably fast for our prompts. Nano needed retries and was no faster, and 3.5 Lightning was slower. None of the four we tried (Nano 30B, 3.5 Lightning, Super 120B, Ultra 550B) accepts images on Token Factory.
```

**Which Nebius platform capabilities were most valuable to your project and how?**
```text
Token Factory's serverless, OpenAI-compatible API was our whole Nebius footprint, and that was the point: we never provisioned or scaled GPUs.

- One endpoint, one key: Hermes Agent ships Nebius as a built-in provider, so the agent and our own Python client (OpenAI SDK, JSON mode, temperature 0) call the same base URL.
- Models switched by name: the model is one env var. That let us time Nano, 3.5 Lightning and Super on the real pipeline, and test which models accept images, with no code change.
- Reasoning control per request: Token Factory honours reasoning_effort for Nemotron. On our extraction prompt, "low" cut a call from about 12 s to 3.4 s; turning thinking off cut it to 1.3 s but got the people wrong. That knob lets us trade speed for accuracy per step.
- Two models on the same endpoint: Nemotron Super handles the reasoning; Gemma 3 27B only turns screenshots into text.
- No GPU instances: the app runs on a small GCP VM, deployed by CI. Hermes' scheduled jobs call Token Factory from there: the 8:00 briefing and a sync every 10 minutes.
```

**How likely are you to recommend running Nemotron on Nebius to other developers? (1-10)**
```text
8/10. Setup took minutes: an OpenAI-compatible API, a built-in Hermes provider, and model switching by name. Nemotron Super followed detailed extraction and tool-use rules well enough to build on. It would be a 9-10 with a vision-capable Nemotron and lower latency for Super.
```

**How would you rate your experience running Nemotron inference on Nebius compared to previous environments? (1-10)**
```text
8/10. There were no GPUs, drivers or model downloads to manage. Our existing OpenAI client and Hermes worked unchanged, and moving between Nemotron sizes was one setting. It lost points for latency (about 12 s per Super call on our extraction prompt, most of it reasoning) and for needing a second, non-Nemotron model for images.
```

**What additional features or improvements would have made the Nemotron on Nebius experience more effective?**
```text
- Vision: a Nemotron that reads images on Token Factory, so screenshots don't need a second model.
- Speed: lower latency or a faster tier for Super, because an agent step plus extraction chains several calls.
- Schema-enforced output: structured output that holds to a JSON schema, so field names can't drift.
- A capability table per model: image input, JSON mode, tool calling, reasoning controls and context length. We learned "no image input" from 400 errors and that reasoning_effort works by testing it.
```

**What do you most hope to see from the Nemotron team next?**
```text
- A multimodal Nemotron on Token Factory. Scam messages often arrive as screenshots.
- A faster Super-class model for agent loops.
- Strong Malay-English (Manglish) support. Our users are in Malaysia, and messages there mix both languages.
```

**Did you use Tavily in your project?**
```text
Yes
```

**Which AI tools have you leveraged while working on this project?** *(confirm before pasting)*
```text
Claude Code (Anthropic) for most of the coding, code review and the specs, and OpenAI Codex for some coding and testing. Inside the product: Hermes Agent and NVIDIA Nemotron on Nebius Token Factory.
```

---

# Testing instructions for judges (judges-only)

Paste into the form's testing-instructions field if it has one. If not, save this section as a file and upload it under **Upload a File** (judges only). Replace `<password>` first.

```text
Demo: https://troth-nebius-nvidia.duckdns.org
Log in with any username and the password: <password>

It's a shared demo with sample data (a student applying for an NVIDIA internship). It resets every night at 19:00 UTC, so change anything you like. Replies take 10-20 s because the model reasons first; a message check takes 1-2 minutes.

Five things to try:
1. Needs attention: "Send NVIDIA application" is at risk. Click it under Open loops to see What it depends on, and the History line where Dr. Lim's email moved his letter.
2. Chat: type "I told Aiman I'd send him the hackathon slides by Thursday, but I can only finish them once Nadia sends me the demo video." Then click the new loop to see the exact words it came from and what it depends on.
3. Waiting for your yes: an email from someone new (Mahsuri Labs) waits as a suggestion. Click Add or Ignore.
4. Check a message (top right): paste the test sample below, click Check, and open the evidence graph when it finishes.
   TEST SAMPLE (not a real message): Dear investor, this is T. Rowe Price Group Sdn. Bhd., the Malaysian branch of T. Rowe Price. Our new fund pays a fixed 12% monthly return, approved by the Securities Commission. Register at troweprice-my-invest.com and transfer your deposit to our Malaysian account before Friday. Contact our advisor at +60 12-000 5678.
5. Chat again: "What's urgent?", "Rename the charger one to Return Aina's laptop charger", "Draft a thank-you email to Sarah for the interview slot", then "yes". The draft lands in the demo Gmail's Drafts; nothing is ever sent.

Optional: email trothdemo@gmail.com from any address with a request ("could you send me the slides by Thursday?"). Within 10 minutes it appears under Waiting for your yes.

The Telegram bot only answers its owner's account, so the video shows it.
```

---

# Before you press Submit
- [ ] The video is uploaded and its link is in **Project details**.
- [ ] The password is only in Additional info or the uploaded file, never on the public page.
- [ ] The AI-tools answer is what you actually used.
- [ ] The two eligibility boxes are true for every teammate.
- [ ] Builders & Brews city: only if you attended an in-person event.
