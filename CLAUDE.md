# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of standalone HTML quiz applications for learning and competitive exam preparation. There is no build system, package manager, or test framework — each `.html` file is a fully self-contained single-page app with embedded CSS and JavaScript.

## Running

Open any `.html` file directly in a browser. No server or build step required.

## Architecture

### File Roles

- **app.html** — "QuizLab": simplest quiz app with flat category-based questions and a timer
- **main.html** — "QuizLab — Learn & Level Up": adds difficulty tiers (easy/mid/hard), user auth via localStorage, and a points/leveling system
- **quiz.html** — "QuizMaster Pro": similar to main.html with difficulty tiers, user profiles, and a leaderboard
- **inter quiz.html** — "ExamEdge Pro": competitive exam platform (TNPSC, SSC, RRB, Banking, UPSC, GATE, CAT, NDA) with explanations and multi-answer support
- **manju.html** — variant of inter quiz.html with the same exam categories and structure

### Question Data Formats

Two distinct formats are used across files:

**Simple format** (app.html):
```js
{ q: "Question text", options: ["A","B","C","D"], ans: 2 }
```

**Difficulty-tiered format** (main.html, quiz.html):
```js
// Categories contain easy/mid/hard arrays
{ q: "Question text", o: ["A","B","C","D"], a: 2 }
```

**Exam format** (inter quiz.html, manju.html):
```js
// Supports multiple correct answers + explanations
{ q: "Question text", o: ["A","B","C","D"], c: [1], e: "Explanation text" }
```

### Common Patterns

- **Screen-based navigation**: sections toggled via `.active` class or `display:none/block`, no router
- **State**: plain JS variables for quiz state; `localStorage` for user profiles, scores, and leaderboard persistence
- **Styling**: dark theme using CSS custom properties (`:root` vars), Google Fonts loaded via CDN, animated gradient backgrounds
- **No external JS dependencies** — everything is vanilla JS
