# Travel posts

How to turn the author's raw trip notes into a travel post. Reference posts: `content/posts/portugal-trip-2026/`, `content/posts/italy-trip-2026/`, `content/posts/japan-trip-2026/`.

The notes usually arrive as a rough bullet log (often a Notion export `.md`) plus photos in a temporary folder at the repo root, e.g. `portugal-blog/`.

## Structure

- Headers are `# Day 1: <short title>`, `# Day 2`, and so on. **No calendar dates** in headers. The short title is optional, only when the day has a clear theme ("Day 7: Cascais").
- For multi-city trips, plain city headers (`# Lisbon`, `# Porto`) are fine between days.
- Intro paragraph: where, roughly when and how long, then "partly for me to come back and reminisce, partly for anyone looking for recommendations". Put `<!--more-->` right after it.
- When the intro or text mentions an earlier trip post, link it (e.g. `[Japan post](/posts/japan-trip-2026/)`).

## Voice

- Short, casual, first person. Sentence fragments are fine ("Work, then went for a boat ride."). Not flowery, no travel-brochure language.
- Keep the author's own verdicts as written: "kinda mid", "yum", "would recommend", "okay-ish", "(yes, I was obsessed)".
- Humor is light and self-aware, usually a short aside in parentheses: a running joke (e.g. cheesecake every other day), "does it even count as a dessert if it's helping you fulfill your protein goals?". Match that, don't overdo it.
- Text faces like `:)` and `:(` are fine. Only when one sits inside parentheses and reads oddly ("(he wasn't :( )") swap it for a real emoji: "(he wasn't 😢)".
- The author is vegetarian, so food notes focus on veg options.

## Editing the notes

- Keep every link the author added (Google Maps, Instagram, booking sites) exactly as given.
- Fix spelling, grammar and place names (accents included: São Bento, Belém). American spelling, see `CLAUDE.md`.
- Don't silently change facts. If something looks wrong (e.g. "7 bridges" for Porto's Six Bridges cruise) or a phrase is ambiguous, make the best call and flag it to the author.
- When the author edits the draft themselves, proofread their new text too.

## Images

- Copy photos into the page bundle with clean lowercase, hyphenated names: fix typos, no spaces (`riberia.jpeg` → `ribeira.jpeg`).
- Write them as `![caption](file.jpeg)`. The render hook turns alt text into the visible caption.
- Place each photo right after the paragraph it belongs to.
- Phone exports around 960×1280 and under ~500 KB are fine. Images are lazy-loaded.

## Thumbnail

- `thumbnail.png`, 1600×900, same layout as the Japan and Portugal ones: cream left panel (`#FBFAE2`) with the bold title "My Trip to / <Country> / (<Cities>)", the avatar + "arsh.wtf" + post date (e.g. "20 Oct") at the bottom left, and a trip photo filling the right ~600px.
- The easiest way is to build it with Python/PIL, reusing the avatar and byline area cropped from an existing thumbnail.

## Wrapping up

- Run `hugo` to check the build.
- Delete the temporary notes folder only when the author asks, and ask before committing or pushing.
