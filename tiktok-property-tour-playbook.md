# Full Circle: "Floating Host" TikTok Property Tour Playbook

A repeatable format for short property tour videos. You appear as a cut-out talking head "floating" over a walkthrough of the property. The editing workflow borrows from Brooke Lacey's approach on *How I AI* ("Claude cuts my TikTok"). She records raw on a phone, Claude Code with FFmpeg and Whisper turns that into a captioned, jump-cut video, and comments become the brief for the next script.

---

## 1. The core idea

**The property is the star and you are the narrator.** The walkthrough footage fills the frame. Your talking head sits in a corner and does three jobs a silent tour can't:

1. **Context.** "This is the one with the heated mudroom."
2. **Honesty.** "The second bedroom is small. Here's how I'd use it."
3. **Trust.** Viewers see a real person who knows the property and answers questions.

### About humor

You don't need to be funny, but you do need personality. Aim for **warm and a little dry**, not jokes.

- **One light beat per video, at most.** For example: "Yes, that's a clawfoot tub. No, it doesn't come with bubbles."
- **Make the humor about yourself or the situation, never about the property.** If you joke about a flaw, it reads like you're hiding a bigger one. Be plain about flaws instead.
- **Never joke about tenants, neighbors or neighborhoods.** This is both a brand rule and a Fair Housing rule (see section 7).
- In this format, being specific does the work humor would. "There are 14 outlets in this kitchen. I counted." is more memorable than a joke.

---

## 2. Video anatomy (30–60 seconds)

| Time | Beat | On screen | You say |
|---|---|---|---|
| 0–2s | **Hook** | Strongest shot of the property, already moving | One line that stops the scroll (see hook bank) |
| 2–5s | **The facts** | Exterior or main room, with a text card showing price, beds/baths and town | "2-bed in Burlington, $1,850, heat included." |
| 5–40s | **The walk** | Continuous tour in walking order, with a cut every 2–4s | One sentence per room, only what the footage can't show |
| — | **Honest note** | The weak spot, shown clearly | "Here's the catch:…" |
| last 5s | **CTA** | Best shot again, plus a link or contact card | "Link in bio to apply. Questions go in the comments and I answer all of them." |

**Rules of thumb**

- **Give the price in the first 5 seconds.** It's the main thing renters want to know, and hiding it costs you viewers.
- **Never let footage play without a reason.** If you have nothing to say about a room, give it 1.5 seconds or skip it.
- **Show the "honest note" on camera.** It's the beat most likely to make people trust you and comment.

---

## 3. Hook bank

Rotate through these and track which ones hold viewers (section 8).

- "This is the cheapest [2-bed] I've listed in [town] this year."
- "Heat's included. That's the whole hook. Okay, fine, let's look around."
- "Three things I love about this apartment and one thing I don't."
- "You asked for a place with a yard under $2k. Here it is." (answering a comment)
- "Most underrated room in this house?" (start on that room)
- "POV: you just signed the lease and you're walking in for the first time."
- "If you work from home, watch to the end."

---

## 4. Shooting

You film the walkthrough and the talking head separately, then combine them in the edit.

### A. Walkthrough footage (the background)

- **Vertical 9:16, 4K if your phone supports it, 30fps.** Lock exposure so it doesn't pump between rooms.
- Use a **gimbal or a slow, steady walk.** The footage should be calm because your talking head brings the energy.
- **Turn on every light and open every blind.** Shoot during the day.
- Shoot **in walking order**: exterior, entry, living, kitchen, bedrooms, bath, storage and laundry, outdoor space, then the weak spot.
- Get a few **detail shots**: faucets, flooring, the view out the best window, the thermostat, closet depth.
- No audio is needed. Mute it in the edit.

### B. Talking head (the overlay)

- Stand in front of a **plain, evenly lit wall.** A green screen is best, but a flat light wall works with AI background removal.
- Frame yourself **from the chest up**, with the camera at eye level.
- Use a **lav or wireless mic.** Audio quality matters more than video quality here.
- Record the whole script in one take. **Pause between lines and redo flubbed lines immediately.** The jump-cut edit removes the pauses and bad takes for you.
- **Option B:** Record the talking head at the property, holding the phone selfie-style, and cut it out later. This feels more authentic but is harder to key cleanly.

### Overlay placement

- Put your cutout in the **lower-left area at about 30–35% of frame width**, sitting above the caption area.
- Keep it **off the right edge**, where TikTok's like/comment/share buttons sit, and **off the bottom ~20%**, where the caption and username sit.
- Add a subtle drop shadow or a thin brand-colored outline so the cutout reads as intentional.
- You can **move the cutout to the other side** when the room's key feature is on the left. Doing this deliberately makes the edit look designed.

---

## 5. Editing workflow (Claude Code + FFmpeg + Whisper)

This is the part borrowed directly from the episode. The goal is to go from raw files to a postable video in minutes, with you reviewing the result rather than doing the editing.

**Inputs per video**

```
tours/2026-10-28-pine-st-2br/
  tour.mp4         # walkthrough footage
  head.mp4         # talking-head recording
  facts.txt        # price, beds/baths, town, availability, link
```

**Edit chain** (ask Claude Code to build this once as a reusable script or skill)

1. **Transcribe** `head.mp4` with Whisper to get word-level timestamps.
2. **Jump-cut** by removing silences longer than ~0.3s, filler words and repeated takes (keep the last take of any repeated line).
3. **Remove the background** from the talking head, using a green-screen chroma key or an AI matte tool for a plain wall.
4. **Fit the walkthrough** to the length of the talking-head audio, matching each room to the line that mentions it where possible.
5. **Composite** the cutout over the tour at the placement in section 4.
6. **Burn in captions**: large, 2–4 words at a time, brand font, inside the safe zone.
7. **Add the facts card** (price · beds/baths · town) at 2–5s and the CTA card at the end.
8. **Export** at 1080×1920, H.264, ~30fps.

A minimal composite step, for reference:

```bash
ffmpeg -i tour.mp4 -i head_cutout.mov \
  -filter_complex "[1:v]scale=iw*0.33:-1[h];[0:v][h]overlay=x=40:y=H-h-420" \
  -c:a copy out.mp4
```

### Teaching it your style

Brooke's main point was that the hard part isn't the cuts. It's teaching the tool your **cadence**. Keep a short `style.md` next to the script and update it every time you correct an edit, for example:

- "Leave a 0.2s beat after the price. Don't cut it tight."
- "Keep the 'here's the catch' line even if it's slow."
- "Don't cut my laugh."

Over time this file becomes the brief, and fewer edits need fixing.

---

## 6. Comments are the content plan

- **Reply to comments with video replies** whenever you can. "Is parking included?" becomes a 15-second reply showing the parking.
- Keep a running list of **questions people ask repeatedly.** Each one is a future hook ("You keep asking about pets, so here's every pet-friendly unit we have").
- Every few weeks, make a **"what $X gets you in [town]"** comparison video using clips from existing tours.

---

## 7. Guardrails (non-negotiable)

**Fair Housing.** Describe the **property, not the person** you imagine living there.

- ✅ "2 bedrooms, 1 bath, 0.4 miles to the bus line, fenced yard."
- ❌ "Perfect for young professionals," "great for a couple," "ideal for empty nesters," "walking distance to [church]," "quiet, mature building," "family neighborhood."
- Don't comment on who lives in the neighborhood, school "quality," or "safety." Link to neutral sources if people ask.

**Accuracy**

- Price, fees, utilities and availability on screen must **match the listing exactly** on the day you post. If something changes, update or archive the video.
- **Don't misrepresent sizes.** Avoid wide-angle tricks that make rooms look much bigger. Lens choice should help viewers see the room, not mislead them.

**Privacy**

- If the unit is occupied, get the tenant's okay and **keep their belongings, photos, mail and faces out of frame.**
- Don't show the unit number or exact address on camera unless the listing already shows it publicly.

---

## 8. Cadence and what to track

- **Start with one tour per week**, the same cadence Brooke uses. Add comment-reply videos in between when they come up.
- Batch-shoot: film the talking heads for 3–4 properties in one session.
- After 10 videos, check these numbers and adjust:
  - **2-second hold rate.** If it's low, the problem is the hook.
  - **Average watch time vs. length.** If it's low, the walk is too slow, so cut more.
  - **Comments per view.** If it's low, add a sharper "honest note" or ask a question in the CTA.
  - **Profile clicks and inquiries.** This is the number that actually matters.

---

## 9. Per-video checklist

- [ ] Price, beds/baths and town on screen by 5s
- [ ] Hook in the first 2s, over a moving shot
- [ ] One "honest note," shown on camera
- [ ] At most one light joke, not at the property's expense
- [ ] Fair Housing language check passed
- [ ] Talking head clear of the right-side buttons and the bottom caption area
- [ ] Captions readable on a phone at arm's length
- [ ] Facts match the live listing today
- [ ] CTA plus a pinned comment with the link or contact

---

*Source for the workflow: [“Claude cuts my TikTok”: How this creator is scaling video with AI](https://www.lennysnewsletter.com/p/claude-cuts-my-tiktok-how-this-creator) (How I AI, Brooke Lacey).*
