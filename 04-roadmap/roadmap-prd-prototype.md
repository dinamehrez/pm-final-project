# Feature Roadmap, Module 4 · StreamLine Spotlight

**Team:** 2 engineers + 1 designer

## Strategic anchors
- **Persona:** Priya, "The Overwhelmed Veteran" (UXR-01, UXR-12), is a 34-year-old heavy viewer and 14-year subscriber. She has watched the catalog grow while her ability to find something good has shrunk. She scrolls for about twenty minutes, closes the app without watching anything, and goes back to a DVD.  By tenure she looks like a Power User, but her current behavior (browse, then leave) looks like a Wanderer.
- **Primary metric:** Browse → Start Playing conversion among Spotlight-exposed users, compared with a non-exposed holdout. The baseline is 29% (Snapshot 1), and the hypothesis targets a 3-point lift.  The 30+ minute session rate (baseline 11%) is a secondary quality check
- **Moment of misery:** Priya sits down to relax and opens StreamLine, but the 15,000-title catalog gives her nothing she wants. She scrolls for about twenty minutes, closes the app without watching anything, and goes back to a DVD.  Her quote from UXR-01: "I open the app, scroll for like twenty minutes, and close it without watching anything. There's 15,000 titles but nothing I actually want."
- **Guardrail:** Power User sessions per week (4.8×) is the guardrail.

## Scoring
| Feature | Value | Effort | Quadrant | Decision | Rationale |
|---|---|---|---|---|---|
| A1 Spotlight Curated Rail | 5 | 2 | Quick Win | Now | A bounded human slate hits Priya's browse-then-leave friction head-on and moves Browse → Play directly. |
| A2 'Why You'll Love This' Label | 3 | 3 | Time Sinker | Cut | Hover doesn't exist on TV or touch, and AI-written reasons clash with the human-led, trust-restoring strategy. |
| A3 Hidden Gem Badge | 3 | 2 | Fill-In | Later | It adds one more label to an already noisy catalog and doesn't tell Priya what to watch tonight. |
| A4 Mood-Based Entry Point | 3 | 4 | Time Sinker | Cut | Only Beth (UXR-09) asks for it, it needs mood tagging across 15,000 titles, and an extra step could hurt time-to-play. |
| A5 Personalized Spotlight Queue | 2 | 5 | Time Sinker | Cut | It rebuilds the algorithm users distrust (UXR-02, UXR-10, BUG-1091) on a pipeline we can't build in three weeks. |
| A6 Spotlight Digest Email | 3 | 3 | Time Sinker | Cut | Tom's UXR-04 shows email works, but it bypasses the in-app browse step our primary metric measures. |
| A7 Curator Profiles | 2 | 4 | Time Sinker | Cut | Priya never asks to follow curators, and profiles and follow mechanics add another surface to browse. |
| A8 Watch Party (Spotlight) | 1 | 5 | Time Sinker | Cut | There is zero evidence in our research, and synchronized playback is a large lift on every TV platform. |
| A9 Advanced Filter Engine | 2 | 3 | Time Sinker | Cut | Priya wants someone to "just tell me what's good" (UXR-12), and filters hand the work back to her. |
| A10 Offline Download (Spotlight) | 1 | 4 | Time Sinker | Cut | It has nothing to do with discovery, and licensing and DRM make it expensive. |

## Roadmap
### NOW, 3-week sprint
- **A1 Spotlight Curated Rail**, A bounded human slate hits Priya's browse-then-leave friction head-on and moves Browse → Play directly.

### NEXT, following 1-2 sprints
- _(none)_

### LATER, backlog
- **A3 Hidden Gem Badge**, It adds one more label to an already noisy catalog and doesn't tell Priya what to watch tonight.

### ✂ Cut List
- **A2 'Why You'll Love This' Label**, Hover doesn't exist on TV or touch, and AI-written reasons clash with the human-led, trust-restoring strategy.
- **A4 Mood-Based Entry Point**, Only Beth (UXR-09) asks for it, it needs mood tagging across 15,000 titles, and an extra step could hurt time-to-play.
- **A5 Personalized Spotlight Queue**, It rebuilds the algorithm users distrust (UXR-02, UXR-10, BUG-1091) on a pipeline we can't build in three weeks.
- **A6 Spotlight Digest Email**, Tom's UXR-04 shows email works, but it bypasses the in-app browse step our primary metric measures.
- **A7 Curator Profiles**, Priya never asks to follow curators, and profiles and follow mechanics add another surface to browse.
- **A8 Watch Party (Spotlight)**, There is zero evidence in our research, and synchronized playback is a large lift on every TV platform.
- **A9 Advanced Filter Engine**, Priya wants someone to "just tell me what's good" (UXR-12), and filters hand the work back to her.
- **A10 Offline Download (Spotlight)**, It has nothing to do with discovery, and licensing and DRM make it expensive.
