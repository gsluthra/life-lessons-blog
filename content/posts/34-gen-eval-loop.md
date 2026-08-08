+++
title = "The Gen-Eval Loop: Getting Quality Outputs from LLMs"
description = "A demonstration of a gen-eval loop across various scenarios"
author = "Gurpreet Luthra"
date = 2026-08-08T07:30:50Z
images = ["/images/general/gen-eval-loop-blog/diagram.png"]


tags = [
    "ai",
    "agentic-ai",
    "opensource",
    "programming",
]

+++

## Introduction

A single prompt to an LLM is a guess. Sometimes it works, but often you end up doing the judging yourself: read the output, figure out what's wrong, prompt again. I wanted to see what happens when an LLM does that judging step too, so both sides keep going back and forth until the work is actually good.

That's the idea behind the **gen-eval loop**. A generator produces something. A separate evaluator grades it against a rubric. The loop repeats with that feedback until the evaluator says pass, or a turn budget runs out. Credit to my colleague [Nikhil Prasad](https://in.linkedin.com/in/nikhilprasad) for introducing me to this pattern.

I presented this concept at [Caizin's](https://caizin.ai/) weekly AI-showcase last week.

## How it works

I built [gen-eval-loop](https://github.com/gsluthra/gen-eval-loop), a small, config-driven harness on top of `claude -p`:

![Generator-Evaluator loop diagram](/images/general/gen-eval-loop-blog/diagram.png "Generator-Evaluator (Gen/Eval) loop")

For every example, I have a generator prompt and an eval prompt (and model). Then I run the program, and it starts looping.

- The **generator** writes its output into a fresh `turn_NNN/` folder each round.
- The **evaluator** runs in its own session and can only see that latest folder. It never sees the generator's reasoning or earlier turns. It writes a `verdict.json` file with a status, score, and feedback.
- The loop feeds that feedback into the next generator turn and repeats.

You can even put a different model in each seat: a faster one to generate, a stronger one to judge. Every task is just a different config file and a pair of prompt files. The harness itself doesn't need any change.

## Results from a real run

I ran it on a UI prototyping task: build a movie-streaming home page, judged against 8 UX heuristics with an all-or-nothing bar. The generator was Haiku, the evaluator was Opus. Over 7 turns, the score moved from 0.375 to 0.875 (0.375, 0.50, 0.81, 0.81, 0.875, 0.88, 0.875). It never fully passed. It kept falling short on one accessibility heuristic. But the trajectory shows real progress: a broken grid layout got fixed by turn 3, and placeholder emoji "posters" turned into real poster art by turn 5.

| Turn 1 (0.375) | Turn 2 (0.50) | Turn 3 (0.81) | Turn 7 (0.875) |
| --- | --- | --- | --- |
| ![Turn 1](/images/general/gen-eval-loop-blog/turn-1.png) | ![Turn 2](/images/general/gen-eval-loop-blog/turn-2.png) | ![Turn 3](/images/general/gen-eval-loop-blog/turn-3.png) | ![Turn 7, final](/images/general/gen-eval-loop-blog/turn-7.png) |

It's also a good way to find out when the evaluator is the weak link. If it passes everything on turn 1, or its feedback is vague, that's a sign the rubric needs work before the generator does.

## Choosing models for each role

The generator and evaluator don't have to be the same model. You can choose a fast (but weak) generator model and a strong eval model, for instance. Different combos have different impacts. See the table below:

| Generator | Evaluator | Advantages | Disadvantages | Typical use case |
| --- | --- | --- | --- | --- |
| Strong | Strong | High-quality drafts and careful review | Highest cost and latency | High-stakes code, security, regulated workflows |
| Same model | Same model, different prompt | Simple architecture, consistent capability | Can share blind spots | Most early production and internal tools |
| Smaller | Stronger | Low-cost exploration, better final judgment | Strong evaluator can become the bottleneck | Many drafts, ranking, design exploration |
| Strong | Specialized or rule-based | Brings domain policies and hard checks | More systems to maintain | Enterprise security, compliance, API standards |
| Smaller | Smaller | Fast and inexpensive | Weak at subtle defects | Low-risk filtering and prototypes |

Rule of thumb: the evaluator should be at least as capable as the generator for the dimension being judged. A strong general-purpose model isn't the only way to satisfy that either. For a narrow code-quality rule, a static analyzer can judge better than any LLM.

## My learnings from this experiment

1. The output definitely improves because of strong evals and the feedback loop.
2. The time (and tokens) consumed in loops is much more than if this was a one-shot prompt, and to get better outputs the generator and eval need fine-tuning.
3. These loops are great for complex tasks, but might be overkill for simple stuff.
4. I also added a self-improving step where the LLM provides feedback on how the Gen-Eval prompts can be made better, based on the learnings from the loops. See the LESSON.md file in some of the examples for this.
5. One cannot judge the quality of an eval if they themselves have limited knowledge of that domain or expertise (for example, how does one judge whether an eval is great or mediocre for UX decision-making if they have never studied the craft of UX?)

## Further reading

- [Anthropic: Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps)
- [AI Heroes: The generator-evaluator harness and the Claude Agent SDK](https://www.ai-heroes.co/en-us/blog/long-running-agent-harness-claude-agent-sdk-2026)
- [Addy Osmani: Long-running agents](https://addyosmani.com/blog/long-running-agents/)
- [IBM: What Is Loop Engineering?](https://www.ibm.com/think/topics/loop-engineering)

## Try it

The repo has nine worked examples, from a four-line poem to a Java crypto reviewer to the movie-streaming run above with screenshots. There's also a short slide deck if you'd rather skip the code: [github.com/gsluthra/gen-eval-loop](https://github.com/gsluthra/gen-eval-loop).
