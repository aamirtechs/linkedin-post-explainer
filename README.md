# LinkedIn Post Explainer

**Explain, don't generate.**

Paste a LinkedIn post. Get what it is actually arguing, what evidence it stands on, how much of it is slop or bait, whether a reply is worth your time, and three reply angles with short human drafts.

One self-contained HTML file. No build step, no server, no account, no paid API.

## Why now

LinkedIn is drowning in generated text, and readers know it:

- Over **40% of long-form LinkedIn posts are now AI-generated** (Pangram, July 2026, reported by CNN, Oct 18, 2026).
- In **August 2026** LinkedIn rolled out a "seems like AI slop" flag, and it was **clicked over 1 million times in its first two weeks**. Flagged low-quality AI content is distributed less.
- The tools that flooded the feed got there by generating comments at scale. In a slop crackdown, a faster comment generator is a liability, not an advantage.

Nobody built the reading side. Every major tool writes for you. None of them explains the post first. This one does.

## How it differs from comment generators

| | Comment generators (Engage AI, Taplio Engage, Commenter.ai) | LinkedIn Post Explainer |
|---|---|---|
| Core job | Write a comment for you | Explain the post so your reply is yours |
| First output | A draft | The argument, the evidence and a verdict |
| Slop awareness | None, and their output can read as slop | Slop and bait check on the post, flags quoted |
| Connection to LinkedIn | Extension reads your feed | **None. Paste-mode only** |
| Posting | Draft or one-click insert | Draft-only, copy is your choice |
| Price model | $17 to $69 per month | Free, local, optional bring-your-own key |

## Safety design (the headline feature)

LinkedIn's User Agreement, section 8.2, prohibits software that scrapes the site, modifies its appearance or automates activity on it. Extensions in that grey zone carry real account risk. This tool is built to stay out of it entirely:

- **Paste-mode only.** You copy a post and paste it in. The tool never connects to LinkedIn, never opens your feed and never reads a page.
- **Local-first.** The analysis engine is plain JavaScript in the single HTML file. Your pasted post is processed in your browser and goes nowhere.
- **Draft-only.** The tool produces drafts. It cannot post, insert, like or follow anything. Publishing stays a human decision, in LinkedIn, by you.
- **Bring your own key, optionally.** The one optional network feature uses **your own** free Google AI Studio key, stored only in your browser's local storage, sent only to Google's API when you press the enhance button. No key, no problem: the local analysis is complete without it.

## Features

- **The argument in plain words**: the main claim, the supporting points, and every piece of evidence found in the post (percentages, money figures, numbers with units, named sources, study and report mentions, links), each quoted in context.
- **Slop and bait check**: an AI-slop signal score from 0 to 100 built from generic phrases, emoji load, hashtag stuffing, listicle padding and exclamation load, plus engagement-bait detection (reader questions, "agree?" prompts, comment prompts), with every flagged item quoted.
- **A verdict**: Reply worth it, Skim, or Skip, with the reason in one line.
- **Three reply angles**, each grounded in a quoted sentence from the actual post.
- **Three draft replies**, one per angle, short and specific, with a tone toggle: Agree and add, Respectful pushback, or Ask a real question. Drafts never open with generic praise and never insert credentials or a sales pitch.
- **Sample post button** so the tool demonstrates itself in one click.
- **Optional Gemini enhancement** with your own key, for a deeper second read on top of the local analysis.

## How to run

1. Download or clone this repo.
2. Open `index.html` in any modern browser. That is it.
3. Paste a post, press **Explain this post**.

No install, no dependencies, no server. It also works offline for the local analysis.

## Testing

- The analysis script passes `node --check`.
- Node tests cover the engine on the sample post: evidence detection finds the percentage, bait detection finds the closing reader question, and a deliberately generic paragraph scores far higher on slop than the sample.
- **Untested:** the Gemini enhancement call is implemented against Google's documented API shape but has **not** been tested with a live key. Treat it as beta. The local engine, which is the product, is fully tested and fully offline.

## Roadmap

- **v1.1**: Saved history of explained posts, kept in local storage only.
- **v1.2**: A printable one-page breakdown for coaching and team use.
- **Later, with care**: an MV3 side-panel companion that reads **only the post the user explicitly clicks**, still draft-only, still no feed scraping, no automation and no posting. If LinkedIn's rules make that unsafe, it does not ship.

## License

MIT. See `LICENSE`. Copyright 2026 Amir Hussain.

LinkedIn is a trademark of LinkedIn Corporation. This project is not affiliated with, endorsed by or connected to LinkedIn.
