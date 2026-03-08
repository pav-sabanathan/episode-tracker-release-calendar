# Decision: Move Footer Links to Settings on Mobile

**Version:** Pre-V2 Polish  
**Date:** March 2026  
**Status:** Resolved

---

## The Question

How should Privacy Policy, Terms of Service, and 
Send Feedback links be surfaced on mobile without 
causing layout issues?

---

## The Problem

A footer containing Privacy Policy, Terms of Service, 
and Send Feedback links was implemented on the Home 
screen following standard desktop web conventions.

On Android Chrome (tested on OnePlus 13), the footer 
was consistently pushed below the visible viewport 
when the browser's address bar was showing, requiring 
users to scroll to see it. The content above the 
footer — logo, empty state, CTA button — left 
insufficient room for the footer when the address 
bar consumed additional vertical space.

Five separate CSS approaches were attempted:
1. 100dvh height with fixed footer
2. Flexbox space-between layout
3. Absolute positioning within relative container
4. Reducing header and content gap progressively
5. Combination of the above with Android-specific 
   padding adjustments

Each fix either resolved the issue in one state 
(address bar visible) while breaking it in another 
(address bar hidden), or introduced new layout 
jumping behaviour as the address bar appeared 
and disappeared on scroll.

---

## Root Cause

The underlying issue was not a CSS problem but a 
design pattern mismatch. Footer links are a desktop 
web convention. Native mobile apps and 
mobile-optimised web apps do not use footer links 
on their home screen — they surface legal and 
utility links inside a Settings or Profile screen 
instead.

Continuing to fix the CSS was treating the symptom 
rather than the cause.

---

## Options Considered

**Option 1 — Continue iterating on CSS fixes**
Keep the footer on the Home screen and find a 
CSS approach that handles Android Chrome's 
dynamic toolbar correctly.

Rejected — five attempts produced no stable 
solution, and the Android Chrome toolbar behaviour 
is a known inconsistency that varies across 
OS versions and Chrome updates. A CSS-only fix 
would be fragile.

**Option 2 — Remove footer from mobile, keep on desktop**
Hide the footer on mobile (max-width: 768px) 
and keep it on desktop where it works correctly. 
Add links nowhere on mobile.

Rejected — Privacy Policy and Terms of Service 
need to remain accessible on all devices for 
legal compliance.

**Option 3 — Move links to Settings on mobile**
Remove the footer from the Home screen on mobile 
entirely and add Privacy Policy, Terms of Service, 
and Send Feedback as tappable rows in the Settings 
page About section.

Selected — this is the correct mobile UX pattern, 
solves the layout problem permanently, and improves 
discoverability by placing these links where mobile 
users instinctively look for them.

---

## The Decision

**Option 3 — Move links to Settings on mobile**

Footer links removed from Home screen on mobile. 
Privacy Policy, Terms of Service, and Send Feedback 
added as tappable rows in the Settings page. 
Settings promoted to a permanent tab in the bottom 
navigation bar to ensure discoverability.

Desktop footer unchanged.

---

## The Outcome

Home screen layout stable on Android Chrome 
regardless of address bar state. Legal links 
accessible on mobile via Settings. No scrolling 
required on the empty state Home screen.

---

## Broader Learning

A recurring UI bug that resists multiple fix 
attempts is often a signal that the design 
pattern itself is wrong for the context rather 
than the implementation. Knowing when to change 
the approach rather than continue iterating on 
the same solution is as important as knowing 
how to write the fix. This mirrors a broader 
product principle — if a feature keeps generating 
support issues, the answer is often to redesign 
the feature, not patch it repeatedly.
