# Grammar Gym

A single-file, offline-first grammar practice app for ESL students.

## Quick Start

Open `index.html` in any modern browser. No build step, no dependencies, no server.

```bash
open grammar-gym/index.html
# or
start grammar-gym/index.html
# or drag into Chrome/Firefox/Safari
```

## How It Works

1. **Import errors** - Paste mistakes from the student's writing or speaking. Supports two formats:
   - Line pairs: `X wrong sentence` / `Y correct sentence`
   - Markdown table: `| wrong | right |`

2. **Practice** - The app selects due items using spaced repetition. Four exercise types:
   - Rewrite (type the correction)
   - Gap fill (fill in the blank)
   - Multiple choice (pick the right form)
   - Correct or not (judge the sentence)

3. **Progress** - Dashboard shows due count, mastery progress, weakest categories, and weekly review.

## Data

All data lives in the browser's `localStorage` under the key `grammar-gym-v1`. Nothing is sent to a server.

- Export your data anytime from the Bank view (JSON download)
- Import a previously exported file to merge data between browsers

## Categories

| Code | Name |
|------|------|
| G-SVA | Subject-verb agreement |
| G-TNS | Tense |
| G-ART | Articles |
| G-PREP | Prepositions |
| G-VP | Verb patterns |
| G-WO | Word order |
| G-REL | Relative clauses |
| G-COND | Conditionals |
| G-COMP | Comparatives/superlatives |
| G-FRAG | Fragments/structure |
| G-PLU | Plurals/countability |
| G-MOD | Modals |
| L-WC | Word choice |
| L-COL | Collocation |
| L-WF | Word form |

## Seed Data

The `seed.js` file contains preloaded errors. On first run (empty state), these are loaded automatically. To add more seed data, add objects to the `window.SEED_ERRORS` array in `seed.js`.

Each seed error can have:
- `category` - one of the category codes above
- `wrong` - the incorrect sentence
- `right` - the correct sentence
- `note` - teacher's hint (optional)
- `fossil` - true if the error is persistent (optional)
- `sess` - session date for logging (optional)
- `similar` - array of similar sentences for reinforcement (optional)

## Voice Features

- **Voice output**: Speaker button next to sentences (Web Speech API, works in all modern browsers)
- **Voice input**: Mic button in rewrite/gap-fill exercises (Chrome only, falls back to typing)

## Spaced Repetition

Intervals: 0, 1, 3, 7, 14, 30, 60 days

- Correct answer: advance to next interval
- Wrong answer: reset to 0 (due today)
- Not sure: re-queues 3 positions later, no penalty
- Confidence 3 (certain) + wrong: marked as blind spot, immediate repeat

Mastery: streak >= 4 AND accuracy >= 80%

## Browser Support

- Chrome (full features including voice input)
- Firefox (voice output only)
- Safari (voice output only)
- Edge (full features)

Voice input requires Chrome/Chromium due to `webkitSpeechRecognition`.

## File Structure

```
grammar-gym/
├── index.html    # Everything: structure, styles, logic
├── seed.js       # Preloaded errors (loaded on first run)
└── README.md     # This file
```

## License

Free to use, modify, and distribute.
