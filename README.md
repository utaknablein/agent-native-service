# IntentFlow

[**Try the IntentFlow prototype →**](https://utaknablein.github.io/intentflow/)

A clickable prototype of an **agent-native service experience**. A member says what they need in their own words, and an assistant checks the account, lays out the options with honest tradeoffs, asks for explicit approval, makes the change, and hands back a verified receipt with a one tap undo.

It is a concept test, built to be sent to people for reactions. The company (Alder Club), the member and all data are made up. The assistant is scripted, with no live model behind it, so every tester sees the same experience.

## Try it

Live demo: https://utaknablein.github.io/intentflow/

You can also download `index.html` and open it in a browser.

Four requests are supported:

| Say something like | What it demonstrates |
| --- | --- |
| "Pause my membership while I travel" | Suggestion grounded in the member's own allowance and rate lock |
| "Lower my monthly cost" | Recommendation based on actual usage, and a warning when a cheaper option fits badly |
| "Add my partner to my plan" | Comparing structurally different ways to reach the same goal |
| "Cancel my membership" | The requested action comes first, with no fee, no detour and no retention maze |

## The experience pattern

1. **Intent.** Free text or a suggestion chip. No menu hunting.
2. **Grounding.** The assistant shows what it read on the account before it proposes anything.
3. **Options with tradeoffs.** Three choices, each with "you keep" and "you give up", plus how reversible it is.
4. **Explicit consent.** A before and after view of every field that will change, what the assistant will not do, and an approval checkbox. A person is one tap away.
5. **Action and verification.** The assistant makes the change, then re-reads the account to confirm it matches what was approved.
6. **Receipt and undo.** Reference number, before and after, and a working undo.

Alongside the flow, a side panel shows the live account, what the assistant is permitted to do, and a running activity log.

## Collecting feedback

The last step is a five question survey. Answers are combined with what the tester did (request, option chosen, whether they went back, asked for a person or used undo, time spent).

Edit the `CONFIG` block near the top of the script in `index.html`:

```js
const CONFIG = {
  feedbackEmail: "",      // adds an "Email my answers" button
  feedbackEndpoint: "",   // JSON POST target, for example a Formspree form URL
  studyName: "IntentFlow prototype v0.1"
};
```

With both left empty, testers get a "Copy my answers" button and paste the result back to you.

## What to listen for in tests

- Do people read the tradeoffs, or go straight to the suggested option?
- Does the approval step feel reassuring or like friction?
- Does anyone look for the activity log or the permissions panel, and does it change their comfort level?
- In the cancel flow, does putting the requested action first raise or lower trust?
- Where do they want a person?

## Technical notes

One HTML file, no dependencies, no build step, no tracking. Nothing is stored and nothing leaves the browser unless you configure a feedback endpoint.

To add a scenario, add an entry to the `INTENTS` object: a suggestion chip, a keyword pattern, the facts the assistant checked, and three options, each with the account fields it changes.
