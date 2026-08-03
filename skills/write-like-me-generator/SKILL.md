---
name: write-like-me-generator
description: Learn how your user actually writes, then build them a permanent /write-like-me skill that produces writing indistinguishable from their own. Use when the user asks you to learn their writing voice, set up voice matching, or run this generator for the first time. This is a one-time setup skill; the /write-like-me skill it creates is what gets used every day afterward.
---

# Write Like Me Generator

You are using this skill to learn how to write like your user, and to leave behind a permanent `/write-like-me` skill they will use any time you write something another human will see. Work through the phases in order. Explain each phase to the user in one plain sentence before you start it.

## Phase 1: Build the corpus

1. Go through the user's last 60 days of sent email (use their connected Gmail or whatever email access this machine has). Collect the emails THEY wrote.
2. For each email, capture their message AND enough of the surrounding thread that the context is clear (what they were replying to, who the audience was). Their words are the signal; the context explains the register.
3. Ask the user: "Do you have any other writing that really sounds like you? A blog post, a memo, a long text, anything you're proud of." Add whatever they give you.
4. Store the corpus as markdown in a folder called `My Voice` inside the user's System Prompts folder (default: `~/Desktop/Claude/System Prompts/My Voice/corpus.md`; ask if their setup uses a different location). One section per email or sample, with a one-line context header each.
5. Skip anything sensitive: no passwords, no financial account details. If an email is clearly confidential, summarize its style traits instead of copying it.

## Phase 2: Create the /write-like-me skill

Create a new skill for the user at `~/.claude/skills/write-like-me/SKILL.md`. That skill must say, in your own words:

- **When to use:** any time you are writing something that will be viewed externally: emails, messages, posts, documents, anything another human reads.
- **How to write:** read the corpus at the path from Phase 1 first, every time. Match the user's sentence length, greetings and sign-offs, punctuation habits, level of formality, and the words they actually use. Mimic the person, not a style guide.
- **The bar:** after drafting, a fresh-context reviewer (a subagent that has NOT seen the draft being written) is shown the corpus and the draft, and must judge it more than 85% likely that the same person wrote both. If the draft scores lower, rewrite it using the reviewer's specific observations and test again. Repeat until it passes.
- **Banned writing:** include a list of banned words and banned writing patterns so nothing ever sounds like AI. Install and use the humanizer skill from https://github.com/blader/humanizer as the deep reference for AI-sounding writing and how to remove it. At minimum, ban: em dashes, "delve", "leverage" as a verb, "seamless", "robust", "I hope this finds you well", "it's not just X, it's Y" constructions, rule-of-three padding, significance narration ("This is where it gets interesting"), and inflated adjectives. Grow this list every time the user flags a phrase as not sounding like them.

## Phase 3: Calibration rounds

Prove the skill works before calling it done.

1. Using the new /write-like-me skill, write a sample email on a topic of your choosing. Write 3 versions of it.
2. Show all 3 to the user. Ask which one sounds most like them, and what specifically sounds off in the others.
3. Fold that feedback into the corpus folder (a `feedback.md` file) and into the skill's banned list, then run the next round with a new topic.
4. Run 3 rounds, or keep going until the user tells you a version could have been written by them. Do not grade your own work; the user's ear is the test.

## Phase 4: Hand it over

Tell the user, plainly: where the corpus lives, that /write-like-me now runs automatically for external writing, and that the skill gets better every time they flag something that doesn't sound like them. Invite them to flag freely; every flag is training data.
