# Copilot instructions

## Build, test, and lint

- The project is a standalone `index.html`; there is no build step, package manager, test runner, or linter.
- To run it, open `index.html` directly in a browser. No server or dependencies are required.
- For a focused manual smoke test, start the quiz, answer one question correctly and one incorrectly, then finish the quiz and confirm the score, feedback, progress, and results screen.

## Architecture

- The HTML, CSS, quiz data, and application logic all live in `index.html`.
- The `questions` array is the source of truth for question text, answer options, correct-answer indices, and explanatory facts. Quiz rendering and scoring use its length rather than a separate question count.
- The script maintains the current question index, score, and whether the current question has been answered. `showQuestion`, `selectAnswer`, and `showResults` update the UI and control the quiz flow.
- CSS custom properties define the shared palette; `prefers-color-scheme: light` overrides them for light mode. The same variables theme the space background, including its inline SVG hex pattern.

## Codebase conventions

- Keep the app self-contained: do not add a framework, external asset, server requirement, or dependency for ordinary quiz changes.
- Add or edit question content in the `questions` array. The `correct` value is a zero-based index into that question's `answers`.
- Build answer buttons from the question data in `showQuestion`; use the existing correct/incorrect classes and feedback status element for answer feedback.
- Preserve accessible native buttons, visible keyboard focus, focus movement to the question heading between steps, live score and feedback announcements, and progress-bar ARIA values when changing quiz behavior.
- Keep theme changes in the CSS custom properties and their light-mode overrides; respect the existing reduced-motion media query for animations.
