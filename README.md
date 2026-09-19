# LIFE: Every Choice Has a Cost

A browser-based, single-player life simulation where every choice has a cost. Manage school, work, money, health, needs, relationships, travel, and unexpected events across 30 in-game days.

## Features

- 30-day simulation across two acts
- Act I school life (Days 1–15)
- Act II adult life (Days 16–30)
- Jobs selected through education and reputation
- AED cash, loans, repayments, interest, and bankruptcy
- Health, energy, hunger, hydration, hygiene, and mood management
- Groceries, activities, locations, opening hours, and travel
- NPC relationships, reputation, messages, and daily interaction limits
- Random positive, neutral, and negative events
- History/feed of decisions and outcomes
- Detailed final report card
- Responsive layout suitable for desktop and mobile browsers

## How to Play

1. Enter a name, starting country, age, and personality.
2. Start with AED 100 and your initial groceries.
3. Use **Places** to travel around town and **Activities** to make choices.
4. Eat, drink, sleep, and shower regularly while balancing school, work, money, and relationships.
5. Use the phone for the bank, messages, and job information.
6. Use **Skip Day** when appropriate, but remember that daily needs and debt interest are applied once per day.
7. Complete Day 30 or reach a game-over condition to see the final report.

## Game Structure

- **Act I — School Life:** Days 1–15. School is available and work is locked.
- **Act II — Adult Life:** Days 16–30. School is removed, work opens, and the best available job reflects education and reputation.

There is no playable Day 31.

## Technologies

- HTML5
- CSS3
- Vanilla JavaScript

No backend, build step, framework, external library, or installation is required.

## Project Structure

```text
LIFE-game/
├── index.html       # Game markup and UI containers
├── style.css        # GitHub Pages stylesheet entrypoint
├── styles.css       # Existing visual design system
├── script.js        # Game state, rules, rendering, and interactions
└── README.md
```

The game uses no image or icon assets, so additional asset folders are not required.

## Running Locally

Open `index.html` in a modern browser. For a local static server, run one of these from the repository root:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## GitHub Pages

1. Push the repository files to GitHub.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select `main` and `/ (root)`, then click **Save**.
5. Open the published Pages URL shown by GitHub.

All references are relative, so the project works when hosted under a repository subpath.

## Screenshots

Screenshots can be added later under `screenshots/` and linked here. Suggested captures are the start screen, main game screen, activities, phone, travel, friends, and final report card.

## Sources / References

- MDN Web Docs, HTML: https://developer.mozilla.org/docs/Web/HTML
- MDN Web Docs, CSS: https://developer.mozilla.org/docs/Web/CSS
- MDN Web Docs, JavaScript: https://developer.mozilla.org/docs/Web/JavaScript
- GitHub Pages documentation: https://docs.github.com/pages
- The life-simulation format is general inspiration from management and choice-based simulation games; no code or assets were copied from another project.

## Credits

Developed by rashid-35 and collaborators listed in the project history.

## Future Improvements

- Save and load games with browser storage
- Additional careers and locations
- More events and relationship outcomes
- Accessibility audit and keyboard navigation improvements
- Optional screenshots and gameplay documentation
