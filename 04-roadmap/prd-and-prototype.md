# Spotlight Curated Rail, Simplified PRD (StreamLine)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** Priya, "The Overwhelmed Veteran" (UXR-01, UXR-12), is a 34-year-old heavy viewer and 14-year subscriber. She has watched the catalog grow while her ability to find something good has shrunk. She scrolls for about twenty minutes, closes the app without watching anything, and goes back to a DVD.  By tenure she looks like a Power User, but her current behavior (browse, then leave) looks like a Wanderer.

## 1. The Big Picture
- **Vision:** Give viewers like Priya a short, human-picked slate they can trust, so a night of scrolling becomes a movie started within minutes.
- **Press release:** StreamLine Spotlight: Tonight's best picks, chosen by people, not algorithms

We all know the feeling: you sit down to relax, open the app, and scroll through thousands of titles until the evening is gone. StreamLine Spotlight ends that. A short, hand-picked slate now sits at the top of the homepage, with a one-line note from a real person on why each film is worth your time. There's no endless scroll, no autoplaying trailer, and no algorithm guessing what you want. You can pick something and press play within minutes.

For viewers who have spent years watching the library grow while finding something good got harder, Spotlight is a simple promise: we've done the looking so you don't have to. The catalog hasn't changed, but now there's a place to start.
- **Success metric:** Browse → Start Playing conversion among Spotlight-exposed users, compared with a non-exposed holdout. The baseline is 29% (Snapshot 1), and the hypothesis targets a 3-point lift.
- **Guardrail:** Power User sessions per week, currently 4.8×, with a 5% tolerance. Mobile DAU (1.49M) is the backup check on overall base health.

## 2. The Details
### User stories
- As Priya, a long-time viewer, I want a short slate of hand-picked titles at the top of the homepage so that I can stop scrolling and choose what to watch tonight.
- As Priya, I want a one-line human-written note on each pick so that I can trust why it's worth my time without leaving the app.
- As Priya, I want to tap a pick and start playing right away so that my evening begins within minutes instead of ending in a DVD.
- As a tired evening viewer, I want the rail to stay quiet, with no autoplaying trailers or sound, so that the screen doesn't ruin the relaxing mood I came for.
- As a StreamLine editor, I want to swap the slate and update the notes without a code deploy so that the picks stay fresh.
- As a Product Manager, I want exposed users compared with a holdout group so that I can see whether Spotlight really lifts Browse → Start Playing.
- As a Product Manager, I want Power User sessions per week tracked alongside the lift so that I can confirm we haven't hurt our existing loyal base.
### Screens to build
- Entry point: Homepage with the Spotlight rail. The rail sits at the top, with 5–7 cards (art, title and the one-line human blurb) and no autoplay or trailer audio. This is where Priya sees a bounded slate instead of endless rows. Tracked event: rail exposure, split by Spotlight and holdout users.
- Feature core: Spotlight pick detail. This is the existing title detail screen with the editor's note shown prominently above a single Play button. It's where she gets the reason to trust the pick and decides, without leaving the app. Tracked event: tap from the rail into the detail screen.
- Success: Playback started. This is the existing player, which loads quietly with no trailer. The success event is the Start Playing event that feeds the primary metric (Browse → Start Playing). Tracked event: play start, attributed to Spotlight.
- Design scope: Screens 1 and 2 need new or modified design work. Screen 3 is the existing player, which keeps the sprint inside one designer's capacity.
### Functional requirements
- These thresholds are proposed starting points, not derived from our data. Please confirm them with engineering and analytics.
- Placement: The Spotlight rail is the first content row on the mobile homepage for 100% of exposed users.
- Bounded size: The rail shows exactly 5–7 titles, never more, and does not scroll into additional titles.
- Human blurb: Every title in the rail has a non-empty, human-written note of 140 characters or fewer, and the rail won't publish if any title lacks one.
- No autoplay: The rail triggers 0 autoplay video or audio events.
- Editor control: An editor can change the slate and notes and see them live within 15 minutes, with no code deploy.
- Holdout assignment: Each user is randomly assigned to exposed or holdout (a 10% holdout is a proposal) and stays in that group for the full 12-week window.
- Tracking: Rail exposure, card tap and play start are logged with a Spotlight attribution tag. At least 99% of rail plays carry it.
- Guardrail reporting: Power User sessions per week (baseline 4.8×) is reported daily for exposed versus holdout, with an alert if exposed falls more than 5% below holdout.
### Smart behaviors (Situation → Outcome)
- If a user is in the holdout group, then show the standard homepage with no Spotlight rail.
- If an editor tries to publish a slate with a title missing its note, then block the publish and flag the title.
- If a title in the slate leaves the catalog, then hide its card automatically and alert the editor.
- If the rail fails to load, then show the homepage without it, with no empty placeholder or error.
- If a user taps a rail card, then open the pick's detail screen with the editor's note and a Play button.
- If a user presses Play from a Spotlight pick, then start playback with no trailer and log a Spotlight-attributed play.
- If Power User sessions per week for exposed users fall more than 5% below holdout, then alert the PM.
### Technical constraints
- No recommendation, ranking or personalization service. The slate order is the editor's order, the same for every exposed user.
- No AI or LLM-generated text. Blurbs are plain strings written by people.
- No new database or microservice. Store the slate as one JSON document in your existing remote config, feature-flag or CMS system.
- No per-user taste or profile data in the rail, and no extra per-user reads.
- No changes to the player, search or existing homepage rows. Insert the rail as one new component and reuse the existing card, detail and playback components.
- No new analytics pipeline. Add the three events (exposure, tap, play start) and one Spotlight attribution tag to the existing system.
- No custom A/B platform. Use existing experimentation tooling for the holdout, or a deterministic hash of the user ID if there is none.
- No My List, cross-device sync or resume changes. BUG-1058 and BUG-1061 are separate work.
- No TV or web surfaces in sprint one. Ship mobile only.
- No editor admin UI. Editors change the config directly.
- No blocking network call at app start. Load the rail asynchronously so it doesn't worsen cold-start time (BUG-1110).
- No video or trailer preloading in the rail.
- Assumption to check: The "no new database" rule only works if StreamLine already has a remote config or CMS that supports no-deploy updates. If it doesn't, requirement 5 (live within 15 minutes with no deploy) and the Effort 2 score on A1 both need revisiting.

## 3. The Logistics
### Features out
- Algorithmic or personalized ordering of the slate (A5), because users distrust the algorithm (UXR-02, UXR-10, BUG-1091).
- AI-generated blurbs or hover labels (A2), because they clash with the human-led strategy and hover doesn't exist on TV or touch.
- Mood-based entry, Hidden Gem badges and advanced filters (A4, A3, A9), because they add steps or labels to a catalog that needs fewer choices.
- Curator profiles and follow (A7), because Priya never asks for them and they add another surface to browse.
- Digest email, Watch Party and offline download (A6, A8, A10), because they bypass the in-app browse step or have no supporting evidence.
- A "save to My List" button on cards, until the Critical sync bug (BUG-1058) is fixed, so saved picks don't vanish across devices.
- Homepage or search redesign beyond inserting the rail.
### Edge cases & safety guard
- Unhappy paths
- If a title in the slate is removed from the catalog, hide its card and alert the editor. If fewer than 5 titles remain, alert the editor and keep the rail visible.
- If the rail's data fails to load or times out, show the homepage without it. No spinner, error banner or empty box.
- If cover art fails to load on a slow connection (BUG-1104), show a title-and-blurb card so the pick is still readable.
- If the slate isn't refreshed on schedule, keep the last valid slate and alert the editor.
- If the editor publishes an empty or oversized slate, reject it with a clear error.
- If a user has already finished a pick, still show it, but flag the case for V2 (BUG-1121 shows finished titles lingering, so avoid adding more of that confusion).
- If playback fails after a tap, return the user to the detail screen with a retry option, and don't send them back to the homepage as in BUG-1042.
- If the holdout assignment fails, default the user to the holdout so the exposed group isn't contaminated.
- What it must NEVER do
- Never autoplay video or audio from the rail (BUG-1077, UXR-05).
- Never show more than 7 titles or let the rail scroll into an endless list.
- Never publish a pick without a human-written note, and never present AI text as human.
- Never use an algorithm or per-user data to order or choose the slate.
- Never show a pick that can't be played.
- Never move a user between exposed and holdout during the 12-week window.
- Never slow the app's cold start (BUG-1110) or change Power Users' existing rows in ways that threaten the 4.8× guardrail.
### Decision log
- Decision 1: Hand-picked slate, no algorithm or AI
- Choice: Editors pick titles and write plain-text blurbs. The slate is the same for every exposed user.
- Rejected: Personalized queue (A5) and AI "why you'll love this" labels (A2).
- Why: Users distrust the algorithm (UXR-02, UXR-10, BUG-1091), and a ranking or AI pipeline can't be built in a 3-week sprint with 2 engineers.
- Revisit when: The Browse → Play lift is proven and editorial capacity becomes the bottleneck.
- Decision 2: No "save to My List" button on rail cards
- Choice: Cards go to detail and playback only.
- Rejected: A save action on each card, which would complete Stage 4 of the journey.
- Why: The Critical sync bug (BUG-1058) means saved picks disappear on the TV, as Ken experienced (UXR-06). Adding the button would send more users into a known failure.
- Revisit when: BUG-1058 is fixed.
- Decision 3: Mobile-only launch
- Choice: Ship the rail on the mobile app first.
- Rejected: Launching on TV, or on mobile and TV together.
- Why: Our baseline (Browse → Play 29%) comes from mobile-only data (Snapshot 1), so mobile is the surface we can measure. Supporting TV as well would exceed a 3-week sprint for 2 engineers.
- Trade-off: Priya's evening context is probably TV, so the first read may understate the effect for her. TV parity stays a Should-Have.
- Revisit when: The week-4 read shows a lift, or TV baseline data becomes available.
### Evals
- These thresholds are proposed targets. We have no baseline for time-on-task, so confirm them with analytics.
- Accuracy: ≥ 99% correct renders. A render is correct when the rail shows the editor's intended slate, every title is playable, and every title has its human-written note. Measured by an automated check on each publish and a daily audit of live rail renders.
- Time-on-task: median time from app open to play start is 3 minutes or less for exposed users, and lower than the holdout. Priya's baseline is about twenty minutes of scrolling (UXR-01), but our snapshots have no time-to-play metric. Add one before launch so there is a baseline.
- Safety: zero violations and no guardrail breach. That means 0 autoplay video or audio events from the rail, 0 unplayable picks shown, 0 users moved between exposed and holdout, and Power User sessions per week within 5% of the 4.8× baseline. Measured from event logs and the daily guardrail report.

## MoSCoW scope
- **Must:** Fixed-size slate on the homepage: One rail, near the top, with a small fixed number of titles (propose 5–7, to validate). A bounded choice is the whole fix for Priya's 15,000-title overload.; Hand-picked titles, no algorithm: Editors choose the titles through a simple config or CMS-lite, with no ranking logic. Users distrust the algorithm (UXR-02, UXR-10).; One-line human-written blurb per title: Plain text, no AI. Without it the rail looks like the trending rows Wanderers already ignore (61% of their mix).; Standard card to play: Art, title and blurb, with a tap that goes to the existing detail or playback flow.; No autoplay or trailer audio on the rail: This avoids repeating BUG-1077 and Dana's UXR-05 complaint.; Editor can swap the slate without a code deploy: Otherwise the rail goes stale in week one.; Exposure tracking and a holdout group: Required to measure Browse → Start Playing against the 29% baseline and to check the Power User sessions guardrail (4.8×). Without it there's no go/no-go.; One launch surface: I'd pick mobile, because Snapshot 1 is mobile-only and measurable. Priya's own context is probably TV, so this is a decision for you.
- **Should:** TV surface, if mobile ships first and capacity allows.; Named critic byline on each pick.; Scheduled slate rotation (daily or weekly).; Graceful hiding of titles that leave the catalog.
- **Could:** Archive of past slates.; A proper editor UI replacing the config.; Editor-facing analytics per pick.; A/B testing of blurbs.; Motion and artwork polish.
- **Won't (now):** Algorithmic or personalized ordering (A5, BUG-1091).; AI-generated blurbs or hover labels (A2).; Mood entry, badges or filters (A3, A4, A9).; Curator profiles or follow (A7).; Email, watch party or offline (A6, A8, A10).; A "save to My List" button on cards, until the Critical sync bug (BUG-1058) is fixed. Otherwise saved picks vanish on the TV, as they did for Ken (UXR-06).; Homepage or search redesign beyond inserting the rail.

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
