# Strategic Discovery Map (Module 1)

## Responses
- **Write one feature from the map that, if an engineer asked “why is this a priority for our 12-week roadmap?”, you honestly could not give a strategic answer for.:** Plant/fish growth (under Motivation).

I added it because many water apps have a virtual pet or plant. I have no evidence that your users want it or that it keeps people coming back. Nobody has said who the app is for, what problem it solves first, or what success looks like in 12 weeks. It's also costly: it needs artwork, animation and game rules, and it only pays off once people already log water every day. Logging, a daily goal and reminders handle that part.

To be fair, most of the map has the same problem. It's a list of features apps like this usually have, not a plan built around your goals. "Friends," "Wearables" and "Weather adjust" would be just as hard to defend. If you tell me who the app is for and the one result you want in 12 weeks, I can redo the map around that and mark what's essential and what can wait.
- **Write one feature that looks “correct” for the app but has zero strategic weight, you have no idea if it helps the company make money or whether a single user actually asked for it.:** Weather-based adjustment (under Features → Goals).

It looks right because it sounds smart and personal: drink more on hot days. But I have no strategic case for it:

No user asked for it. None of the user needs on the map call for it. The closest one, "adjust for heat, exercise, pregnancy," is something I wrote myself, not something users told us.
No link to money. I can't say it would get anyone to pay, upgrade or stay longer. A hot day doesn't happen often enough to bring people back each day.
It doesn't fix the real risks. The biggest problems on the map are people losing interest and logging feeling like a chore. This feature does nothing for either.
It isn't free to build. It needs a weather service and access to the user's location, and someone would have to justify the extra water amounts with health evidence. That ties into the "goal formulas lack medical backing" problem.
To be honest, I made up the whole map from what water apps usually have. None of it is based on real users or business goals. If you can share who it's for, how it will make money, or any user feedback, I can sort the map into what's backed by evidence and what's just a guess.
- **Compare V3 to your Step 1 baseline. What changed, and is the output objectively better, did the AI get smarter, or did your added PM knowledge (JTBD, effort/impact, retention) force it to be useful?:** What changed between the first map and V3

First map: six branches of features (Logging, Goals, Reminders, Insights, Motivation, Settings). There was no target user, no problem, no business model and no risks. It was basically a list of features from competing apps.
V3: a specific user (busy adults 25–40 who forget), with a main goal in the middle. Features are now traced back to user jobs and friction, sorted by effort vs. impact, and some are marked "avoid." It adds monetization tradeoffs, retention risks with fixes, five debates to settle and questions for the sprint.
Is it objectively better?

For a discovery sprint, yes, by measures you can check:

Every item now traces back to a user need, a friction point or a business reason.
It makes choices. The first map ranked nothing; V3 says do first, validate, later and avoid.
It names tradeoffs and open questions instead of treating everything as good.
It admits that nothing has been tested with users.
But it's still not validated. It's a better set of guesses, not proof.

Did the AI get smarter?

No. It was the same model in the same conversation, a few minutes apart. Telling it to "forget past context" didn't reset anything, and your earlier challenges probably shaped V3 too.

What actually made the difference?

Mostly your prompt. Each part of your brief filled a specific gap in the first map:

"Busy adults 25–40 who forget" gave a real target to rank against. Without a target, nothing can be ranked.
Jobs-to-be-done forced features to answer "why does anyone want this?"
Effort vs. impact forced choices, which is how the virtual pet ended up under "avoid."
Monetization and retention brought in the business view the first map ignored.
"Flag tensions" pushed it to show disagreements instead of hiding them.
I already knew all of these frameworks at the first step. I just didn't use them, because a vague prompt gets the most generic answer. Your brief set the standard the answer had to meet.

To be fair to V3, I did add some of my own judgment. The ideas that success means users leave, and that the friction is physical (no bottle nearby), weren't in your brief.

Bottom line: the model's ability stayed the same. The quality jumped because the prompt contained product strategy. The real test is whether a sprint with real users confirms or overturns V3's guesses.
- **Key takeaway: how does this prove the PM’s role is to think while the AI’s role is to execute?:** It demonstrates the split, it doesn't prove it. Here's what the session actually shows, and where the claim breaks.

What supports the split

Three maps, same model, minutes apart. The only variable was how much product thinking was in the prompt. V1 got a list of competitor features. V3 got a target user, JTBD, effort/impact, monetization and a request for tensions — and produced a usable discovery artifact. The mechanism is simple: the model optimizes hard against the standard in the prompt. A vague prompt has a low standard, so it returns the average of every water app that exists. Your brief didn't make it smarter; it gave it something to be correct about. That's the PM contribution — defining what correct means.

Where the split is too clean

The AI did think. It invented the "if the job is building a habit, success means users leave, which kills the subscription" tension — that wasn't in your brief. And when you asked it to name its own weakest feature, it did that honestly. Execution that can critique itself isn't pure execution.
The PM thinking here was framing, not evidence. You never named a real user, a number, a revenue model or a constraint. That's the difference between thinking and deciding — and deciding is what the AI couldn't do for you.
Execution wasn't neutral. Choosing which items land in "avoid" is a judgment call made inside the AI.
The takeaway I'd actually write down

The PM's job is to own the constraints and the consequences. The AI's job is to search the space inside them, fast, and to argue back. What can't be delegated isn't thinking — it's accountability. If V3 is wrong, no one gets fired; you do. That asymmetry, not intelligence, is what separates the roles.
