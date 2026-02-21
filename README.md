# rank-meme-humor

Ranks memes by humor across three dimensions: comic surprise (how well the meme subverts expectations), cleverness (the ingenuity of its comedic construction), and economy of delivery (how cleanly it lands without over-explanation). Accepts memes as images or text and scores them so funnier memes rank higher.

## Input

The function accepts an array of 2 or more memes. Each meme can be either:

- **Image** — A meme in any standard image format (captioned photos, multi-panel comics, screenshots, image macros, etc.)
- **Text** — A text-based meme (copypasta, tweet screenshots transcribed as text, dialogue formats, etc.)

Both formats can be mixed freely within a single input array. The function evaluates humor without bias toward any particular meme structure or medium.

### Example

```json
[
  "me: I'm going to bed early tonight\nme at 3am: do fish know they're wet",
  "<image of a captioned meme>",
  "recruiter: where do you see yourself in 5 years?\nme: I don't even know what I'm having for lunch"
]
```

## Output

A score distribution array of the same length as the input. Each score corresponds to the meme at the same index, with higher scores indicating funnier memes. Scores are normalized and sum to approximately 1, representing each meme's share of the total humor across the set. The meme with the highest score is the funniest in the group; the meme with the lowest score is the least funny.

### Example

```json
[0.45, 0.38, 0.17]
```

In this example, the first meme is ranked funniest, the second is close behind, and the third trails significantly.

## What It Evaluates

The function evaluates each meme across three core qualities. These qualities work in concert — the highest-ranked memes are those that excel across all three.

### 1. Comic Surprise

The most fundamental engine of humor: the subversion of expectation. This dimension measures the gap between where the audience thinks the meme is going and where it actually goes. Memes that wield irony, absurdity, exaggeration, or surprise to blindside the viewer score high. Memes that arrive at a predictable destination score low. The wider and more delightful the subversion, the stronger the score.

**Scores high:** A meme that sets up a familiar premise and detonates it with a twist you didn't see coming.
**Scores low:** A meme whose punchline is exactly what you expected from the setup.

### 2. Cleverness

The intellectual craftsmanship behind the joke. This dimension measures whether the meme demonstrates ingenuity in how it constructs its humor — through precise juxtapositions, layered meanings, creative recontextualization of templates, or visual-textual interplay that neither element could achieve alone. A clever meme rewards a second look and reveals depth beneath its surface.

**Scores high:** A meme with a double meaning that clicks after a beat of thought, or one that repurposes a well-known format in a way that recontextualizes the original.
**Scores low:** A meme that relies on brute-force randomness or shock value without any underlying craft.

### 3. Economy of Delivery

The discipline of restraint. This dimension measures how cleanly and efficiently the meme lands its joke. Every element — text, image, panels, formatting — should be load-bearing and necessary. A meme that trusts its audience, leaves the joke implicit where appropriate, and delivers with surgical precision scores high. A meme that over-explains, adds redundant context, or uses more than it needs scores low.

**Scores high:** A meme where nothing could be added and nothing could be taken away — every element serves the joke.
**Scores low:** A meme that spells out its punchline in a caption when the image already said it, or uses three panels where two would suffice.

## Use Cases

- **Content platforms** — Surface the funniest memes in a feed to maximize engagement and user delight.
- **Community moderation** — Spotlight the best submissions in meme channels, subreddits, or group chats.
- **Meme competitions** — Provide fair, consistent, multi-dimensional judging for meme contests and tournaments.
- **Content curation** — Automatically filter and rank user-generated meme submissions for newsletters, roundups, or "best of" collections.
- **Research** — Supply a repeatable, structured framework for studying internet humor and comedic effectiveness across formats.

## How It Works

The function uses three vector completion tasks, each targeting one of the evaluation dimensions. Each task frames the memes as candidate responses to a prompt designed to elicit that specific quality of humor:

1. **Comic Surprise Task** — Presents memes as responses to a request for something unexpected and blindsiding.
2. **Cleverness Task** — Presents memes as responses to a request for something intellectually crafted and admirable in construction.
3. **Economy Task** — Uses a precision-focused curator persona to evaluate memes as responses to a request for lean, efficient comedy.

The scores from all three tasks are combined to produce the final ranking, ensuring that memes are evaluated holistically rather than on any single axis of humor.
