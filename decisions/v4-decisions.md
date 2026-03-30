# V4 Product Decisions

**Version:** V4 — Settings & Custom Platforms  
**Shipped:** March 2026

---

## Decision 1 — Suggested Platforms List

**What:** Instead of requiring users to create custom platforms entirely 
from scratch, V4 includes a curated list of 10 suggested platforms that 
can be added with a single tap.

**Platforms included:** Crave, Paramount+, Max / HBO Max, Crunchyroll, 
Sky, NOW TV, Channel 4, ITVX, Peacock, BritBox

**Why these 10:** Selected to reflect the two primary markets Plotify 
is targeting — Canada and the UK. The built-in list (Netflix, Disney+, 
Apple TV, Prime Video, BBC iPlayer) covers the universal tier. The 
suggested list covers the regional tier most relevant to these audiences.

**Trade-off considered:** A longer list (20+ platforms) was considered 
but rejected — too much cognitive load in the UI, and most platforms 
outside this list are niche enough that manual creation is a reasonable 
ask.

---

## Decision 2 — Hex Input with Colour Wheel Picker

**What:** The custom service colour input shows a hex code field by 
default. Clicking the colour swatch opens a colour wheel modal with 
hue/saturation wheel, brightness slider, and a live hex field inside 
the modal.

**Why:** Two user types were considered — users who know their platform's 
exact brand hex code (power users, designers) and users who want to pick 
visually. The hex-first approach serves the former without friction, 
while the colour wheel serves the latter. Making the wheel opt-in via 
the swatch click keeps the default UI clean.

**Alternative rejected:** A preset colour grid (8 swatches) — too 
limiting given that platform brand colours are specific and rarely match 
a preset palette exactly.

---

## Decision 3 — Spoiler-Free Calendar Export as a Toggle

**What:** A toggle in Settings that excludes episode descriptions from 
all ICS exports when enabled. Off by default.

**Why:** Calendar notifications are one of the primary use cases for 
Plotify's ICS export. If a user has notifications enabled on their 
calendar app, an episode description appearing in a notification 24 
hours before watching is a genuine spoiler risk. This is an opt-in 
feature rather than opt-out because most users likely want the full 
context in their calendar.

**Persistence:** Stored in localStorage (V4) — will migrate to 
user_preferences in Supabase in V5.

---

## Decision 4 — Competitor Research Observations (March 2026)

Tested TVCal, Trakt.tv, and TV Time during V4 development week.

**TVCal:** Clean, focused calendar product. Their iCal feed UX is 
the benchmark — feed URL, one-tap Google Calendar button, iCal file 
download, and Yahoo Calendar option all clearly presented. Their 
Webcal implementation (dynamic, auto-updating) is exactly what V5P6 
should replicate. Their app is calendar-first, which is a narrower 
scope than Plotify.

**Trakt.tv:** Most feature-complete competitor. Notable: show detail 
pages with IMDb/RT scores and trailer links (requires TMDb — V5 
candidate), Wrapped-style year-to-date stats (good fit for V6 
alongside badges), social layer with profiles and activity feed 
(post-V6, needs auth foundation). Their VIP paywall is aggressive — 
opportunity for Plotify to offer a cleaner free experience.

**TV Time:** Strong on profile personalisation (display name, profile 
photo, cover photo with show posters). The configurable profile is 
worth incorporating into V5P2's first sign-in profile setup step.

**Key gap identified across all three:** None of them handle the 
guest-to-signed-in transition well. This is a priority to get right 
in V5P2 and V5P4.

---

## Decision 5 — Settings Cog Moves Into Avatar Dropdown Post-Auth

**What:** In V4 the settings cog is visible in the top right header. 
In V5, when a user is signed in, the cog is replaced by the user 
avatar — Settings moves inside the avatar dropdown menu.

**Why:** Avoids two tappable icons competing for the same space in 
the header. The avatar is a more familiar pattern for accessing account 
and settings in authenticated apps. Guest users retain the cog as-is.
