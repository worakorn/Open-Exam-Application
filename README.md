# Open Exam Application

## Introduction

The "Open Exam Application" is a standalone, offline-capable exam system built entirely within single HTML files. It provides a highly flexible platform for creating and taking multiple-choice exams with timed tests, advanced configuration, Computerized Adaptive Testing (CAT), and immediate detailed results with performance analytics.

**Current Version: v3.1 — CISSP Edition with CAT + Dark Mode**

| File | Description |
|------|-------------|
| `exam.html` | Main exam application (v3.1) — ISC² CISSP themed, CAT engine, dark mode |
| `exam-builder.html` | Exam authoring tool (v3.1) — Create and edit JSON exam files |
| `bank/` | Collection of pre-built exam JSON files (CISSP, CC, PDPA, etc.) |

> **Note:** Previous versions (`exam.html` v1.9.2 and `exam-next.html` v2.0.1) have been superseded by the unified v3.1 release which combines and improves all features from both.

## Features

### Core Exam Features
- **Single File Portability:** Entire application in one HTML file — fully offline, zero external dependencies
- **Custom Exam Files (JSON):** Load from local file, URL, or use built-in demo
- **Advanced Setup:** Default, Quick Start, or Custom Domain selection modes
- **Configurable Timer:** Optional time limit with per-question time warnings
- **Back Navigation:** Configurable forward-only or free navigation
- **Progress Tracking:** Visual progress bar with question counter

### Computer Adaptive Testing (CAT)
- **CISSP-Style Adaptive Difficulty:** 10-level difficulty scale (Fundamental → Insanely Hard)
- **Sliding Window Algorithm:** 3-question window adjusts difficulty based on recent performance
- **Smart Stopping Criteria:** Early pass, early fail, mastery detection, max questions
- **Domain Balancing:** Ensures balanced coverage across knowledge domains
- **Real-Time Analytics:** Live difficulty indicator and score tracking during exam

### Performance Analytics
- **Confidence Score:** Rewards fast, correct answers — measures test-taking confidence
- **Domain Breakdown:** Results sorted best-to-worst by knowledge domain
- **Review System:** Review correct, incorrect, and unanswered questions with explanations

### Security & Quality
- **CSP Headers:** Content Security Policy restricting script/style sources
- **XSS-Safe DOM:** All user data rendered via textContent — zero innerHTML injection
- **URL Sanitization:** Protocol validation, localhost blocking
- **Data Integrity:** JSON schema validation, AnswerKey verification, duplicate question detection
- **Dead Code Free:** Audited and cleaned — no unused CSS, JS functions, or polyfills

### User Experience
- **Dark Mode:** Toggle with persistent preference (localStorage)
- **Keyboard Shortcuts:** 1-9 select choices, Enter advances/submits
- **Mobile/Tablet Responsive:** 3 breakpoints (768/600/374px), iOS zoom fix, touch-safe hover, 48px tap targets
- **Mobile-Safe File Input:** Uses native `<label for="">` pattern — works reliably on all mobile browsers including iOS Safari
- **Page Close Guard:** Prevents accidental tab close during exam
- **Accessible:** Focus-visible rings for keyboard navigation
- **Print-Friendly:** Clean results page for Ctrl+P

### Exam Builder
- **Visual Editor:** Create questions with domain, difficulty, choices, and explanations
- **Sectioned Sidebar Layout:** Settings section and question list clearly separated with proper spacing
- **CAT Configuration:** Set min/max questions, pass percentage, enable adaptive mode
- **Domain Percentage Setup:** Configure proportional question distribution with live total indicator
- **Import/Export:** Load existing JSON files and export validated exam packs
- **XSS-Safe:** All rendering via safe DOM construction (textContent + createElement)
- **Dark Mode + Responsive:** Matching theme system, 3 breakpoints (900/768/480px)

## How to Use

1. **Download** the `exam.html` file
2. **Open** in any modern browser (Chrome, Firefox, Edge, Safari)
3. **Load an exam** via URL, local file, or built-in demo
4. **Configure** your preferred setup mode
5. **Take the exam** — answer questions, navigate with buttons or keyboard
6. **View results** — score, confidence, domain breakdown
7. **Review** — check explanations for incorrect/unanswered questions

## Exam JSON Format

See **[bank/README.md](./bank/README.md)** for the detailed JSON schema including CAT configuration fields.

## Disclaimer

**This software is 100% AI-generated.** While extensively tested and hardened, there are no guarantees of perfect functionality. This project is intended primarily for educational purposes. See the Terms of Use within the application for full details.

## Contact

- **Author:** Worakorn Kuruwongwattana
- **LinkedIn:** [https://www.linkedin.com/in/kworakorn/](https://www.linkedin.com/in/kworakorn/)
- **Repository:** [https://github.com/worakorn/Open-Exam-Application](https://github.com/worakorn/Open-Exam-Application)

## Contributors

- **bank4500 (Aj. Bank)** — Contributed 30+ bug fixes and major feature implementations across v1.9.1 through v3.1, including security hardening, CAT integration, dark mode, mobile responsive design, data integrity layer, dead code cleanup, and keyboard accessibility.
