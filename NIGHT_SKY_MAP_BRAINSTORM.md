# 🧠 Night-Sky Constellation — Map System Brainstorm

> Living doc. We're deciding *how tokens actually become stars* on the sky.
> This is the make-or-break architecture decision for Concept 4.

## The core question

Gary asked (correctly): do we use a **real map system** where each crypto has a
fixed location on a star-chart we create — or is it generated per-user / per-view?

The honest answer is: **any of these can work, and they produce different products.**

---

## Approach A — RIGID COORDINATE SKY (the "real map" option)

**How it works**
Every token is assigned a *permanent, deterministic* sky location derived by
hashing its contract address (seeded RNG). PEPE is literally in the same part
of the sky forever, for every user, on every device. The sky is a big navigable
plane (pan + zoom), we just render the visible window.

**Why it's good**
- It's a *real map.* Stable identity: you can learn where things live, talk about
  "the PEPE sector," direct friends to a spot.
- Any user's tokens are a constellation *within a shared universe.* The map is
  the product; wallets/darks corners are just highlights.
- Zoom-in is meaningful: Galaxy (all) → your constellation → token.

**Why it's risky**
- Positions are *arbitrary* — they encode nothing. A fixed map is beautcer but
  informationally static; two random meme coins could sit side by side.

**Bottom line**
This is the "Sky Map as platform" version. Best if we want the map itself to be
the thing — a crypto atlas you navigate.

---

## Approach B — SEMANTIC MARKET-SPACE (data-encoded positions)

**How it works**
Position is *meaningful*, like a scatter plot styled as stars:
- X axis = market cap / liquidity size
- Y axis = age / risk (young+hot up top, aged+stable lower)
- Star brightness = momentum; color = behavior (whale, meme, launch, etc.)

Clusters *naturally* form: meme coins cluster together, majors cluster,
fresh launches cluster in one zone.

**Why it's good**
- Positions encode knowledge. You can literally *see* market structure — the
  "meme quadrant," the "majors zone," the "danger zone" of fresh launches.
- Zoom + clustering do double duty: zoom out = market overview, zoom in = your
  wallet's neighborhood. Your coins are a constellation glowing inside it.

**Why it's risky**
- Tokens *drift* as data changes. Less of a stable "map," more of a living chart.
- Overlap for similar tokens → needs jitter + collision handling.

**Bottom line**
The "Star Map as market telescope" version. Best if we want the sky to be
*both* beautiful and informative — the thing you check to *understand* the market,
not just watch it.

---

## Approach C — DYNAMIC MOOD SKY (fluid/attractor simulation)

**How it works**
A lightweight physics sim: major tokens have "gravity," momentum pushes stars,
hot tokens attract attention rings. The whole sky is alive — stars drift into
clusters of energy and pull apart as things cool.

**Why it's good**
- The most *magical.* Feels like a living organism, not a chart. Perfect for the
  "mood ring" vibe. Shareables are stunning.
- Auto-documents change: incoming capital physically pulls the sky.

**Why it's risky**
- Nothing ever stabilizes — hard to navigate by memory, disorienting for a
  returning user.
- Costs more (per-frame sim on device), harder to test/trust.

**Bottom line**
The "Sky as living organism" version. Best as a *hero mode / share card / idle
screen*, not as the primary navigation.

---

## The zoom flow (shared by all approaches)

The three-level navigation Gary described:

```
LEVEL 1 · THE GALAXY
  All of crypto, faint tubes of constellations. Your portfolio = a glowing
  constellation you can see even zoomed all the way out (a beacon).

LEVEL 2 · YOUR CONSTELLATION (DEFAULT HOME)
  Zoomed in on your coins. The 5-20 stars you hold + the neighbors around them.
  This is the default landing view. Stars twinkle; alerts pulse.

LEVEL 3 · THE STAR (TOKEN)
  One star fills the view. Info card: price, moment, alerts. From here
  "tap through" to the token detail screen.
```

---

## Open questions to decide

1. **Stable map vs living chart?** (A = stable, B/C = alive). This is the big fork.
2. **Is the sky shared or personal?** Is there ONE crypto sky everyone navigates
   (A), or does each user get their own sky of their holdings (B/C)?
3. **What do positions MEAN?** If data-encoded (B), which axes? (mcap×risk?
   age×momentum? something else?)
4. **Where's the line between "map" and "chart"?** The moment we style a scatter
   plot as stars, it's honest. The moment we hash arbitrary positions, it's art.
   Both are valid — but the product is different.
5. **Do tokens stay put week to week?** Returning-users test: close the app,
   come back tomorrow — is your constellation where you left it?
6. **Mobile vs desktop first?** Pan/zoom is natural on touch; on desktop we need
   a gesture language (drag, pinch, click-to-center, search-to-fly).
7. **Empty state** — new user with 0 coins. Do we drop them into "Big Dipper"
   mode (explore the whole galaxy) until they hold something?
8. **Performance budget** — how many stars max? 200 (soft), 2000 (fine), 20k
   (needs canvas/WebGPU). Camera + cull per frame.

---

## My honest recommendation

Start with **Approach B (semantic) for the default front feed** — it's the one
that makes the sky *worth* looking at (it shows you structure, not just stuff),
and it naturally explains "why is my coin HERE?" — because its data put it there.

Then add **A as a "pin/stable sky" layer** later if users want memorability, and
keep **C as the hero share-card / idle animation** because that's where the magic
sells.

But — this is exactly what the mockups decide. Next step is building all three
front-feeds as wireframes so we can feel the difference in our hands.

---

## Related

- `concept4-nightsky-constellation.html` — original night-sky concept
- `concept4b-nightsky-fullset-square.html` — full card set, square corners
