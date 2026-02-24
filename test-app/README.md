# Quiz CLI

## Project Overview
Quiz CLI is a small, interactive command-line quiz game written in modern Node.js (ES Modules). It provides categorized multiple-choice quizzes (JavaScript, Node.js, General Programming) and demonstrates common JavaScript/Node concepts such as:

- ES Modules (import/export)
- Async/await and Promises
- File system operations (reading JSON)
- Readline-based user input handling
- Classes and OOP patterns
- Array methods, destructuring, template literals
- Simple terminal styling using ANSI codes

The repository is lightweight (no external runtime dependencies) and intended as an educational/demo CLI app you can run and extend.

## Setup Instructions
1. Ensure you have Node.js 18+ installed (package.json specifies "engines": ">=18.0.0").
   - Download from: https://nodejs.org/

2. Clone the repository:

```bash
git clone https://github.com/dmytropanov-sa/test-app.git
cd test-app
```

3. Install dependencies:

- There are no external dependencies to install; the app uses built-in Node APIs.
- If you want to use npm scripts, you can still run:

```bash
npm install
```

4. Run the application:

- Via npm script:

```bash
npm start
```

- Or directly with Node:

```bash
node index.js
```

- The entry file has a shebang (#!/usr/bin/env node), so you can make it executable on Unix-like systems and run `./index.js` after `chmod +x index.js`.

## Usage Examples
- Launch the quiz:

```bash
npm start
# or
node index.js
```

- Typical flow:
  1. Choose a category from the presented list (e.g., "JavaScript Basics").
  2. Choose how many questions to answer (All/3/5 depending on availability).
  3. Answer each question by entering the number corresponding to the option.
  4. Press Enter to continue between questions (prompted).
  5. View results and review incorrect answers at the end.
  6. Choose whether to play again.

- Notes:
  - Prompts expect numbers (for selections) or 'y/n' for confirmations.
  - The quiz shuffles questions each run.

## File Structure

- index.js — Main entry point. Loads questions, manages main loop, and coordinates user interaction.
- package.json — Project metadata and scripts (start/test), Node engine requirement, and license.

Data:
- data/questions.json — Quiz content (categories with arrays of question objects). Contains fields: question, options (array), answer (index), explanation (optional).

Source:
- src/
  - colors.js — Terminal color helpers using ANSI escape codes.
  - input.js — Readline-based input utilities (createInterface, prompt, select, confirm, pressEnter).
  - quiz.js — Quiz class and game logic (shuffling, asking questions, showing results).

## Questions data format
questions.json uses a structure like:

- categories: { <categoryId>: { name: string, questions: [ { question, options[], answer, explanation? } ] } }

Example minimal question schema:

```json
{
  "question": "What keyword is used to declare a constant in JavaScript?",
  "options": ["var", "let", "const", "define"],
  "answer": 2,
  "explanation": "The 'const' keyword declares a block-scoped constant..."
}
```

To add or edit quiz content, update data/questions.json. Ensure `answer` is the zero-based index into `options`.

## Dependencies & Environment
- Runtime: Node.js >= 18 (uses node: builtin import specifiers and fs/promises)
- No external npm packages required
- package.json:
  - "start": "node index.js"
  - "test": "node --test" (no tests included — placeholder)

## Implementation Notes & Features
- Uses ES module syntax (package.json has "type": "module").
- Terminal UI:
  - colorized output via src/colors.js (no external libs).
  - Simple ASCII banner and progress bar.
- Input utilities in src/input.js provide reusable prompts for other CLI tools.
- Quiz logic shuffles questions on each run (Fisher–Yates).

## Contribution & Extensibility
- How to contribute:
  - <!-- TODO: Add contribution guidelines (CONTRIBUTING.md) -->
  - Suggested workflow:
    1. Fork repository
    2. Create a feature branch
    3. Submit a pull request describing changes

- Ideas for improvements:
  - Add persistent high-score storage (file or DB).
  - Add timed questions or difficulty levels.
  - Add CLI flags (e.g., non-interactive mode, choose category via CLI args).
  - Add unit tests and CI workflow.

## Testing
- package.json defines a "test" script that runs `node --test`. There are currently no test files included.
- <!-- TODO: Add tests and instructions to run them -->

## License
- MIT (declared in package.json)

## Troubleshooting & Known Limitations
- Requires Node 18+ due to use of the node: protocol imports and fs/promises API.
- No external error-reporting; on unexpected errors the app prints the error message and stack trace and exits.
- If you experience garbled colors on some terminals, you can adjust or disable color helpers in src/colors.js.

## Maintenance & Contact
- Repository: dmytropanov-sa/test-app
- Author/contact details: <!-- TODO: Add maintainer contact or contributor info -->

---

If you would like, I can also generate a CONTRIBUTING.md, a basic test scaffold, or add a GitHub Actions workflow. Reply with which you'd like next.