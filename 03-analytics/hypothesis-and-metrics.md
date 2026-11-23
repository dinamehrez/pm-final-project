# Hypothesis & Success Metrics (Module 3)

## Pre-work · Hypothesis check
- **Role , who you are solving for (from M2):** Pryia the overwhelmed veteran
- **Goal , what this user is ultimately trying to achieve:** pick something she enjoys and start watching within minutes
- **Friction / moment of misery , the specific pain blocking their goal:** Friction: She opens the app, scrolls for about twenty minutes through 15,000 titles, closes it without watching anything, and goes back to a DVD.
- **Current workaround , the external tool or manual process they rely on (M2):** switching to a DVD
- **Problem Hook , your one-sentence framing of the business crisis (M1):** By burying quality beneath 15,000 uncurated titles, StreamLine forces its highest-value viewers to outsource discovery to competitors and third-party apps out of sheer choice paralysis—turning our biggest content asset into a driver of subscriber churn and brand commoditization.
- **Value Proposition , the outcome your initiative promised to deliver (M1):** StreamLine Spotlight turns the app from an overwhelming content warehouse into a trusted editorial authority. Viewers get a bounded daily or monthly slate vetted by named critics, with "Why Watch This" context and a calm, trailer-free UI. The business unlocks its existing 15,000-title catalog without new acquisition spend. It's urgent because the industry has shifted from growth to retention, and enthusiast viewers are hard to win back once they leave.

## Read your data snapshots
- **Does the funnel data confirm your M2 friction point, or does it tell a different story? Note where the numbers align with the qualitative pain you found and where they diverge.:** The funnel partly confirms Priya's friction and partly points somewhere else. I'm reading "M2 friction point" as her twenty-minute scroll that ends in a DVD.

Where it aligns

Browse without play: 71% of visitors browse, but only 29% start playing. That is a 42-pt loss between "looking" and "watching," which is Priya's pattern at scale.
Search is failing: Search-then-play fell from 41% to 34%. This matches the descriptive-query failures (BUG-1080, Lucia's "slow quiet French drama").
Engagement is eroding: DAU is down 21%, and sessions reaching 30+ min fell from 19% to 11%. This is consistent with loyal users drifting away, as Tom did.

Where it diverges

Sessions are getting shorter, not longer: Priya's story is a long, fruitless scroll, but average session length fell 23%. In aggregate, people may be leaving quickly instead of scrolling for twenty minutes. The funnel can't tell us which, because we have no time-in-browse metric.
The biggest drop is before she scrolls: Homepage → Browse loses 29 pts, the largest single step. That points to the homepage failing to invite exploration, which Priya doesn't experience.
Mobile versus TV: The data is mobile-only, and Priya's evening scenario (and the Samsung buffering bug, BUG-1042) is TV. So the snapshot can't confirm her friction directly.
Start Playing → 30+ min loses 18 pts (29% → 11%): The callout reads this as a discovery problem. But 62% of people who start playing don't reach 30 minutes, and the cause could be technical (buffering drops, resume failures) as easily as poor picks. Spotlight would not fix technical causes.

What it means for the solution: The data supports Spotlight for Stages 1–3 (browse → play), but it also suggests curation alone won't recover the 30+ minute drop. Stage 4 and the stability bugs matter more than we assumed.
- **Do the retention patterns align with the workaround your M2 persona used to find content? Note what the Mo. 0→1 drop suggests about the onboarding experience your persona described as frustrating.:** Mostly aligned in direction, but the cohorts don't map neatly onto Priya.

Where it aligns

Bounded curation helps: Spotlight cohorts keep 74–79% at Month 1, against 63–68% for Full Library. They also decay more slowly afterwards (Dec loses 13 then 9 pts, versus Sep's 17 then 12). That supports the idea that choice overload drives departure, which is Priya's problem.
The gap widens: By Month 3, Dec is at 52% versus 34–39% for the Full Library cohorts, so the effect doesn't fade.

Where it diverges

Priya isn't in this data. These are sign-up cohorts, meaning new subscribers. Priya is a 14-year veteran, and her research describes catalog fatigue, not an onboarding complaint. The heatmap can't tell us whether Spotlight retains tenured users like her.
The "12 to 15 points" claim is shaky. Like-for-like, the Month 1 gap is about 11 pts on average (6–16 depending on which cohorts you pair). Full Library was also already declining (68 → 66 → 63).
It isn't a clean test. Spotlight cohorts are Dec–Feb and Full Library cohorts are Sep–Nov. Holiday and New Year sign-ups may behave differently, so seasonality and acquisition mix confound the comparison.

What the Month 0 → 1 drop suggests: Even with Spotlight, 21–26% leave in the first month, and 32–37% do without it. New users likely hit the same "nothing I want" moment early, so the first session may not prove value. But the heatmap doesn't show why. Promo-rate cancellations (the price-sensitive subscribers in your hook) would look identical, so I'd treat the onboarding explanation as a hypothesis.
- **Does the LTV gap and the content mix (61% trending for Wanderers) confirm the moment of misery your persona described? Note which segment your persona is in and whether the data confirms their pain.:** The data partly confirms Priya's misery, but it also challenges who the persona should be. I'm reading the churn column as −14 and −22 pts, since the minus signs rendered as commas.

Which segment is Priya? The snapshot doesn't say, and she sits between two:

By identity, a Power User. UXR-01 calls her a "heavy viewer" with 14 years of tenure.
By current behavior, a Wanderer. She opens the app, scrolls, and watches nothing. If segments are behavioral, she may be a former Power User who has slid into Wanderer behavior.

Where it aligns

The content mix fits her misery. Wanderers consume 61% trending and only 18% curated. That matches "everything on the home screen is loud and new" (UXR-09) and Priya's "nothing I actually want." Power Users, at 58% curated, are the people who found curated content.
The churn result fits her fix. Exposure to Spotlight cuts Wanderer churn by 22 pts, so bounded, curated picks help the people who aren't finding anything.

Where it diverges

If Priya is a Power User, the data says she isn't the opportunity. Their churn is "low anyway," which contradicts treating her as a flight risk.
The LTV gap is a symptom, not proof. Power Users watch 4.4× more but are worth only 1.7× more ($14.20 vs $8.40). The curated mix may reflect that Power Users are already engaged, not that curation made them engaged.
Your hook assumed "high-value viewers," but the data points at the lowest-LTV segment. Weighting churn improvement by base share and LTV, Wanderers still lead Casuals (about 76 vs 59), but the gap is smaller than the headline suggests. Casuals also contribute the most revenue (about 39%).
The 22-pt result may be biased. We don't know whether Spotlight exposure was random or self-selected, or what period the churn covers.
- **Does the low adoption confirm your persona is burdened by tools they don’t use? Note whether the low scheduling adoption (42%) for coordinators matches your M2 moment of misery.:** _(not filled in)_
- **Does the workflow data match the manual process or hack you documented in M2? Note whether the specific drop-offs or time gaps explain why your persona avoids the digital tool.:** _(not filled in)_
- **Look at the CSAT heatmap. Which specific cell most directly maps to your persona’s friction? Note how the NPS trend justifies the urgency of your M1 Problem Hook.:** _(not filled in)_

## Step 3 · Craft your hypothesis
- **Qualitative evidence (from M2) , quote the specific friction / moment of misery for your persona:** Qualitative evidence (M2):

Priya, 34, heavy viewer and 14-year subscriber (UXR-01):

"I open the app, scroll for like twenty minutes, and close it without watching anything. There's 15,000 titles but nothing I actually want. I ended up going back to a DVD."

Moment of misery: She scrolls about twenty minutes through 15,000 titles, closes the app without watching anything, and reverts to a DVD.

Corroborating quote (UXR-12, older focus group): Three of six participants said the number of choices made them anxious and they'd rather someone "just tell me what's good tonight."
- **Quantitative evidence (from M3) , name the metric or data point that confirms the pain; cite the number:** Quantitative evidence (M3):

Primary data point: In Snapshot 1, 71% of homepage visitors browse titles, but only 29% start playing. That is a 42-pt drop between browsing and watching, which is Priya's "scroll and leave without watching."

Supporting data points:

Snapshot 3: Wanderers are 41% of the base and watch 1.1× per week. Their content mix is 61% trending and 18% curated, which matches "nothing I actually want."
Snapshot 1: Search-then-play fell from 41% to 34%, and sessions reaching 30+ min fell from 19% to 11%.

Caveat: The funnel is mobile-only, and it doesn't show how long users browse before leaving. The data confirms the pattern but not Priya's twenty-minute scroll specifically.
- **Persona , role, goal, and the friction you confirmed in the reconciliation steps:** Persona: Priya, "The Overwhelmed Veteran" (UXR-01, UXR-12)

Role: A 34-year-old heavy viewer and 14-year subscriber who has watched the catalog grow while her ability to find something good has shrunk. By tenure she looks like a Power User, but her current behavior (browse, then leave) looks like a Wanderer.

Goal: To pick something she'll enjoy and start watching within minutes, so the evening feels relaxing instead of like a chore.

Friction confirmed: She browses a large, trending-led catalog and leaves without playing anything. Quantitatively, 71% browse but only 29% start playing, and Wanderers (61% trending, 18% curated) watch just 1.1× per week.

Not confirmed by the data:

The twenty-minute duration, because the funnel has no time-in-browse metric.
Her TV context, because the snapshots are mobile-only.
An onboarding problem, because her research never mentions one.
- **Problem you are solving , one sentence describing the specific friction this initiative removes:** Problem you are solving:

Spotlight removes the choice overload that leaves viewers like Priya browsing a 15,000-title, trending-led catalog and leaving without playing anything, because nothing in it tells them what is worth watching.
- **Strategic outcome , what behaviour change do you expect, and how does it map to retention / revenue / churn?:** Behavior change: Viewers like Priya go from browsing without playing to choosing a Spotlight pick and pressing play within minutes. The measurable shift is a higher Browse → Start Playing rate (today 29%) and more 30+ minute sessions (today 11%).

Mapping to business outcomes:

Churn: Spotlight exposure cut churn by 22 pts for Wanderers (41% of the base) and 14 pts for Casuals (37%). Power Users already have low churn.
Retention: Spotlight cohorts keep 74–79% at Month 1, versus 63–68% for Full Library cohorts, and they decay more slowly afterwards.
Revenue: Revenue shows up through retained subscribers, not higher prices. Each saved Wanderer keeps $8.40 per month and each saved Casual keeps $11.40. The catalog is already licensed, so no new content spend is needed.

Caveats to state: Both the churn and cohort results may be biased by self-selection and seasonality. The Wanderer upside is large in volume but low in LTV, so it depends on keeping many users, not a few high-value ones.
- **Primary success metric (initiative signal) , the leading indicator that tells you the gap is closing:** Primary success metric: Browse → Start Playing conversion among Spotlight-exposed users, starting from a baseline of 29% (Snapshot 1).

Why this one:

It measures Priya's friction directly. It is the step where she browses and then leaves without playing.
It's a leading indicator. It moves within days, long before the lagging results in churn (−22 pts for Wanderers) or Month 1 retention (63–68% today).
It's measurable now. The funnel already tracks it.

How to read it: Track it for Wanderers separately, since they are the target segment, and compare exposed users to a non-exposed holdout to avoid the selection bias flagged earlier. The gap is closing when exposed users' Browse → Play rate rises above that of non-exposed users and holds.

Guardrail: Sessions reaching 30+ min (baseline 11%). If plays rise but long sessions don't, users are picking Spotlight titles and then abandoning them, which would point to technical causes such as buffering or resume bugs rather than curation.

I haven't set a numeric target, since we have no evidence to ground one.
- **Guardrail metric (product signal) , the metric that must NOT drop; it protects your existing base:** Guardrail metric: Power User sessions per week, currently 4.8×.

Why this one: Power Users are 22% of the base and the highest LTV at $14.20. They already have low churn, so Spotlight isn't aimed at them. The risk is that putting a curated, bounded surface on the home experience disrupts the habits that keep them engaged. If their weekly sessions fall, we're trading a loyal base for a recovering one.

Backup: Mobile DAU (currently 1.49M, down 21% over six months) as the overall base-health check. Even if the initiative helps Wanderers, it shouldn't accelerate that decline.

Correction to my last answer: I called 30+ minute sessions a guardrail, but it's better treated as a secondary quality signal for the primary metric, since it checks whether plays turn into real viewing. The guardrail should protect the existing base, which is what Power User sessions do.
- **Decision window , how much time or data before you scale, pivot, or kill? minimum threshold to proceed?:** Decision window: 12 weeks (about 90 days, matching the snapshot window), with a read at week 4.

Week 4: the primary metric (Browse → Play) is readable within days to weeks.
Week 12: enough time for the first exposed cohort to reach Month 3 retention.

Minimum threshold to proceed (proposed, not derived from our data):

Primary: Spotlight-exposed Wanderers show a statistically significant Browse → Play lift of at least 3 pts over a non-exposed holdout (baseline 29%).
Guardrail: Power User sessions per week stay within 5% of 4.8×.
Quality check: 30+ min sessions (baseline 11%) rise along with plays.

Decisions:

Scale: All three thresholds are met, and Month 1 retention for exposed users is above the holdout.
Pivot: Plays rise but 30+ min sessions don't, which points to technical causes (BUG-1042, BUG-1061) instead of curation. Or the lift appears only in Casuals, not Wanderers.
Kill: There is no significant lift by week 12, or the guardrail is breached.

Caveat: The 3-pt lift and 5% tolerance are placeholders. Our snapshots give no basis for exact numbers, so you should confirm them with your data and analytics team before treating them as commitments.
- **Draft your full hypothesis sentence , one to three sentences; quote the metric, name the persona, name the outcome:** Based on Priya's account of scrolling twenty minutes through 15,000 titles and ending up back on a DVD (UXR-01, UXR-12), and on data showing that 71% of visitors browse but only 29% start playing, with Wanderers consuming 61% trending and 18% curated content, I believe that solving choice overload with a bounded, critic-curated Spotlight slate for Wanderer-like viewers such as Priya will result in more browsing sessions turning into plays, as measured by a 3-point (about 10% relative) increase in Browse → Start Playing conversion among Spotlight-exposed users versus a holdout, from the 29% baseline. I will protect Power User sessions per week (currently 4.8×, tolerance 5%) and will make a go/no-go decision after 12 weeks.

The 3-point lift and the 5% tolerance are placeholders, as flagged earlier. The statement also assumes the effect shows up in Wanderers, which is where Snapshot 3 shows the strongest response.
