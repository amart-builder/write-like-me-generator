# Write Like Me Generator

A Claude Code skill that learns how you actually write, then builds you a permanent `/write-like-me` skill so everything Claude writes for you sounds like you, not like AI.

## What it does

1. **Builds a corpus of your real writing.** It reads your last 60 days of sent email (with the thread context that explains each one) and asks you for any other writing that sounds like you: a blog post, a memo, anything. The corpus lives in a `My Voice` folder on your Mac.
2. **Creates your personal `/write-like-me` skill.** From then on, any time Claude writes something another human will see, it reads your corpus first and mimics you: your sentence length, your greetings, your punctuation, your words.
3. **Holds itself to a real bar.** Every draft is checked by a fresh reviewer that compares it against your corpus. If the reviewer isn't more than 85% convinced the same person wrote both, Claude rewrites and tests again.
4. **Never sounds like AI.** The skill carries a banned list of AI-sounding words and patterns, built on the excellent [humanizer](https://github.com/blader/humanizer) skill, and it grows every time you flag a phrase that isn't you.
5. **Calibrates with you.** It writes sample emails in rounds of three, you pick the one that sounds most like you, and it learns from your feedback until you can't tell its writing from yours.

## Setup

Paste this into Claude Code:

```
Install the write-like-me-generator skill: clone this repo to a temp folder, copy the
folder containing SKILL.md into ~/.claude/skills/write-like-me-generator, delete the
temp clone. Then read that SKILL.md and follow it start to finish.
```

That's it. The generator walks you through the rest in about 15 minutes.
