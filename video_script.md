# Troth demo video script (3:00)

Each scene: the page or app to open (heading), what to do, what to say.
The chat message in Scene 2 was tested twice against the real model (2026-10-26): both times a promise to Aiman due Thursday, a "waiting on Nadia" loop, and the link between them.

## Before you record

- **Timing:** record after the **03:00 nightly reset** (Malaysia time), so the demo starts fresh.
- **Browser:** log in at https://troth-nebius-nvidia.duckdns.org with any username and the `APP_PASSWORD`. Set zoom to 110–125% and close other tabs.
- **Tabs to have ready:**
  - the README architecture: https://github.com/ADAMAMZAR/troth#architecture
  - your Nebius Token Factory console, on its usage page
- **Phone:** open the Telegram chat with the bot and send `/new` before recording.
- **Takes:** record Scenes 2 and 5 a few times. Live AI varies: about 1 run in 5 drops a person, and the official domain is found about 2 runs in 3. Never edit data by hand.
- **Waits:** cut them in editing. Saving takes 15–20 s; the check takes 1–2 min.

---

## Scene 1 · 0:00–0:15 · Browser: Troth dashboard

**Do:** Start on the dashboard. Let the top bar show **"… need you today"**, then move the mouse slowly down **Needs attention**.

**Say:** "This is Troth, a personal AI for the things that slip: the promise you made, the reply you're waiting on, and the message pretending to be someone you trust. It remembers what's unfinished and warns you before it slips."

## Scene 2 · 0:15–0:50 · Browser: Troth dashboard → Chat panel

**Do:**
1. Click the chat box (**"Type a message…"**) and type:
   `I told Aiman I'd send him the hackathon slides by Thursday, but I can only finish them once Nadia sends me the demo video.`
   Press **Enter**. Cut the wait.
2. Point at the reply, then at the new loops highlighted under **Open loops**.
3. Click **Send hackathon slides**. Show **Why Troth knows this** (your exact words) and **What it depends on** (Nadia's video).

**Say:** "I just talk to it. Hermes Agent hands my words to Troth, and NVIDIA Nemotron on Nebius Token Factory pulls out the loops: a promise to Aiman due Thursday, something I'm waiting on from Nadia, and the link between them. Every loop keeps the exact words it came from, so I can always see why Troth knows it."

## Scene 3 · 0:50–1:20 · Browser: Troth dashboard → Needs attention

**Do:**
1. Point at **Send NVIDIA application**: *at risk: "Get reference letter from Dr. Lim" is due …, after this*, with its three options.
2. Click that loop under **Open loops**. Show **What it depends on**.
3. Scroll to **History** and point at the line where **Dr. Lim's email** moved the letter's date.

**Say:** "Here's what reminders can't do. I promised Sarah my NVIDIA application, and it needs Dr. Lim's reference letter. His email just moved the letter past my deadline. Troth caught it. Plain rules in code, not the model, flag the promise as at risk and work out my options: ask Dr. Lim, tell Sarah early, or move my date, before I let anyone down."

## Scene 4 · 1:20–1:35 · Browser: Troth dashboard → Waiting for your yes

**Do:** Point at the **Mahsuri Labs** online-assessment suggestion, then click **Add**.

**Say:** "Email from someone new never changes anything on its own. It waits for my yes. And Troth never sends anything: drafts and calendar events wait for my OK too."

## Scene 5 · 1:35–2:15 · Browser: Check a message (button at the top right)

**Do:**
1. Click **Check a message**. In **Paste what they sent you**, paste this, keeping the TEST SAMPLE line visible:
   ```
   TEST SAMPLE for ScamGraph scenario B (clone company). Not a real message.

   Dear investor, this is T. Rowe Price Group Sdn. Bhd., the Malaysian branch of T. Rowe Price. Our new fund pays a fixed 12% monthly return, approved by the Securities Commission. Register at troweprice-my-invest.com and transfer your deposit to our Malaysian account before Friday. Contact our advisor at +60 12-000 5678.
   ```
2. Click **Check**. Briefly show **How the check went** as the steps tick, then cut the wait.
3. On the result:
   - Show the risk level and **Fixed rules set the risk level**.
   - Tap the **Bank Negara** point in the **Evidence graph** so its evidence opens below.
   - Point at a source link under **Claims and evidence**.
   - If this take didn't find the real domain (troweprice.com), record it again.

**Say:** "Some messages aren't who they claim to be. This is a test sample of a clone investment firm. Troth researches who's asking on the live web with Tavily, and Nemotron reads what it finds. The risk level comes from fixed rules, never from the model, and every finding links to its source: here, Bank Negara's alert list and the company's real website."

## Scene 6 · 2:15–2:35 · Phone: Telegram, chat with your Troth bot (optional)

**Do:** Hold the phone next to the screen. Send `/briefing` and show the reply, with the risky payment first. If you skip this scene, give the 20 seconds to Scene 5.

**Say:** "It's the same memory on my phone. Every morning at eight, Troth sends my briefing on Telegram: the risky payment first, then what's due today."

## Scene 7 · 2:35–2:55 · Browser: GitHub README Architecture, then Nebius Token Factory console

**Do:** Show the architecture diagram for about 10 s, then the Token Factory usage page for 2–3 s, so the Nemotron requests are visible.

**Say:** "Under the hood, Hermes Agent is the assistant, calling Troth through 18 MCP tools. Every model call is NVIDIA Nemotron on Nebius Token Factory: Nemotron 3.5 Super VL for the agent, the extraction and screenshots, and Nemotron 3 Super for the scam research, where it measured faster. Tavily brings the evidence."

## Scene 8 · 2:55–3:00 · Browser: Troth dashboard

**Do:** Return to the dashboard and hold for 3 seconds.

**Say:** "Troth: nothing you owe slips through. Try it at troth-nebius-nvidia dot duckdns dot org."
