# Tutor pilot

I want a creator to be able to publish one exercise that a learner can start on the web and finish in Obsidian. My first task for Devin is a recursion exercise about what happens after the base case returns.

## The exercise

Trace `sum(3)`, where `sum(0) = 0` and `sum(n) = n + sum(n - 1)` for positive integers. A learner who answers `0` for both `sum(0)` and `sum(1)` gets a follow-up question: “Which line runs next?” If they say the program has finished, show the paused `return 1 + sum(0)` line and let them revise their prediction. Then give them `sum(4)` to trace unaided.

## First task for Devin

Serve a static course manifest and one versioned exercise, `recursion/return-value@1`. Both clients use the same TypeScript loader and answer checker. A one-time code pairs the Obsidian plugin with the learner’s web session. One Cloudflare Worker and D1 store progress. Each client saves pending events locally and reuses the same event ID on retry.

## Week-one acceptance test

1. Enter `0` for the base case in the browser. Pair a test vault and confirm that Obsidian shows the saved answer.
2. Disconnect the plugin, enter the remaining return values (`1, 3, 6`), and restart Obsidian while offline.
3. Reconnect, replay the final event twice, and refresh the browser. It must show the completed trace, and D1 must contain exactly one copy of that event.

A reviewer should run this in a real browser and Obsidian and attach the recording to the first implementation PR.
