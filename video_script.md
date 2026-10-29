# Troth demo video script (3:00)

Each step: what to do, then what to say while you do it.
The chat message in Scene 2 was tested twice against the real model (2026-10-26): both times a promise to Aiman due Thursday, a "waiting on Nadia" loop, and the link between them.

## Before you record

1. Record after the 03:00 nightly reset (Malaysia time), so the demo starts fresh.
2. Log in at https://troth-nebius-nvidia.duckdns.org with any username and the `APP_PASSWORD`.
3. Set browser zoom to 110–125%. Close other tabs.
4. Open two tabs: the README architecture (https://github.com/ADAMAMZAR/troth#architecture) and the Nebius Token Factory usage page.
5. On your phone, open the Telegram chat with the bot and send `/new`.
6. The day before, run the Scene 5 message once on the demo (the 03:00 reset clears it). It hasn't been tested against the real model yet. Use it only if it finds maybank2u.com.my and scores HIGH or above.
7. Record Scenes 2 and 5 a few times. Live AI varies: about 1 run in 5 drops a person. Never edit data by hand.
8. Cut the waits in editing. Saving takes 15–20 s; the check takes 1–2 min.

---

## Scene 1 · 0:00–0:15 · Troth dashboard

1. **Do:** Start on the dashboard. The top bar shows "… need you today".

   **Say:** "This is Troth, a personal AI for the things that slip: the promise you made, the reply you're waiting on, and the message pretending to be someone you trust."

2. **Do:** Move the mouse slowly down Needs attention.

   **Say:** "It remembers what's unfinished and warns you before it slips."

## Scene 2 · 0:15–0:50 · Troth dashboard, chat panel

1. **Do:** Click the chat box. Type the message below. Press Enter. Cut the wait.

   ```
   I told Aiman I'd send him the hackathon slides by Thursday, but I can only finish them once Nadia sends me the demo video.
   ```

   **Say:** "I just talk to it."

2. **Do:** Point at the reply. Then point at the new loops under Open loops.

   **Say:** "Hermes Agent hands my words to Troth, and NVIDIA Nemotron on Nebius Token Factory pulls out the loops: a promise to Aiman due Thursday, something I'm waiting on from Nadia, and the link between them."

3. **Do:** Click "Send hackathon slides". Point at "Why Troth knows this", then "What it depends on".

   **Say:** "Every loop keeps the exact words it came from, so I can always see why Troth knows it."

## Scene 3 · 0:50–1:20 · Troth dashboard, Needs attention

1. **Do:** Point at "Send NVIDIA application" in Needs attention (marked at risk).

   **Say:** "Here's what reminders can't do. I promised Sarah my NVIDIA application, and it needs Dr. Lim's reference letter."

2. **Do:** Click that loop under Open loops. Scroll to History. Point at the line where Dr. Lim's email moved the date.

   **Say:** "His email just moved the letter past my deadline. Troth caught it."

3. **Do:** Scroll back up to Needs attention. Point at the Options line.

   **Say:** "Plain rules in code, not the model, flag the promise as at risk and work out my options: ask Dr. Lim, tell Sarah early, or move my date, before I let anyone down."

## Scene 4 · 1:20–1:35 · Troth dashboard, Waiting for your yes

1. **Do:** Point at the Mahsuri Labs suggestion.

   **Say:** "Email from someone new never changes anything on its own. It waits for my yes."

2. **Do:** Click Add.

   **Say:** "And Troth never sends anything: drafts and calendar events wait for my OK too."

## Scene 5 · 1:35–2:15 · Check a message

1. **Do:** Click "Check a message" (top right). Paste the message below. Keep the TEST SAMPLE line visible.

   ```
   TEST SAMPLE (fake bank warning). Not a real message.

   Maybank: Your account will be frozen today at 11:59 PM because your eKYC is incomplete. Verify now at maybank2u-secure-my.com to keep using Maybank2u. Need help? Call 03-0000 1234.
   ```

   **Say:** "Some messages look exactly like the real thing. This is a test sample of a fake bank warning: a threat, a deadline, a link."

2. **Do:** Click Check. Show the steps ticking. Cut the wait.

   **Say:** "Troth researches who's asking on the live web with Tavily, and Nemotron reads what it finds."

3. **Do:** Point at the risk level and "Fixed rules set the risk level".

   **Say:** "The risk level comes from fixed rules, never from the model,"

4. **Do:** Click the Maybank point in the Evidence graph. Point at the official site under Claims and evidence.

   **Say:** "and every finding links to its source: here, Maybank's real site, maybank2u.com.my, not the link in the message."

If the take didn't find the real site (maybank2u.com.my), record it again.

## Scene 6 · 2:15–2:35 · Phone, Telegram (optional)

Skip it? Give the 20 seconds to Scene 5.

1. **Do:** Hold the phone next to the screen. Send `/briefing`. Show the reply.

   **Say:** "It's the same memory on my phone. Every morning at eight, Troth sends my briefing on Telegram: the risky payment first, then what's due today."

## Scene 7 · 2:35–2:55 · README, then Token Factory

1. **Do:** Open the README tab. Show the architecture diagram.

   **Say:** "Under the hood, Hermes Agent is the assistant, calling Troth through 18 MCP tools. Every model call is NVIDIA Nemotron on Nebius Token Factory:"

2. **Do:** Open the Token Factory tab. Show the Nemotron requests.

   **Say:** "Nemotron 3.5 Super VL for the agent, the extraction and screenshots, and Nemotron 3 Super for the scam research, where it measured faster. Tavily brings the evidence."

## Scene 8 · 2:55–3:00 · Troth dashboard

1. **Do:** Open the Troth tab. Hold for 3 seconds.

   **Say:** "Troth: nothing you owe slips through. Try it at troth-nebius-nvidia dot duckdns dot org."
