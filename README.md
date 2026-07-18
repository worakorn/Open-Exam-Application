# 🎓 Open Exam Application

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-3.1--CISSP-green.svg)](#)
[![Offline Capability](https://img.shields.io/badge/offline-100%25-blue.svg)](#)

A standalone, offline-capable exam system built entirely within single HTML files. Crafted with vanilla HTML, CSS, and JavaScript, it provides a highly flexible platform for creating, customizing, and taking multiple-choice exams.

Featuring timed tests, advanced user-driven configurations, Computerized Adaptive Testing (CAT), and in-depth performance analytics.

---

## 🌟 Key Contributors

This application is co-authored and maintained by:

*   **Worakorn Kuruwongwattana** (Original Creator) — LinkedIn: [kworakorn](https://www.linkedin.com/in/kworakorn/)
*   **bank4500 (Aj. Bank)** (Core Contributor) — Architected the unified **v3.1 CISSP Edition**, consolidated the Stable/CAT engines, established strict CSP & XSS safety patterns, and built the responsive dark mode interface.

---

## 🚀 Version 3.1 — CISSP Edition with CAT + Dark Mode

The latest release merges the stable fixed-length exam features and the cutting-edge Computerized Adaptive Testing (CAT) engines into a single, high-performance, responsive HTML file (`exam.html`), deprecating all previous dual-file setups.

| File | Type | Description |
| :--- | :--- | :--- |
| **[`exam.html`](./exam.html)** | Web App | Main exam application — ISC² CISSP themed, CAT engine, dark mode, zero dependencies. |
| **[`exam-builder.html`](./exam-builder.html)** | Authoring | Exam builder tool — Visual editor to create, configure, and export JSON exam banks. |
| **[`bank/`](./bank/)** | Directory | Collection of pre-built exam JSON banks (CISSP, CC, PDPA, etc.). |
| **[`legacy/`](./legacy/)** | Directory | Superseded standalone versions (`exam.html` v1.9.2 and `exam-next.html` v2.0.1) kept for reference. |

---

## ✨ Features

### 📦 Core Exam Engine
*   **Single-File Portability:** Runs entirely in the browser with no server, CDNs, or Google Fonts dependencies. Fully offline-first.
*   **Custom Exam Loader:** Drag and drop or browse any local JSON exam file, or load it from a remote URL.
*   **Advanced Exam Setup:** Choose from **Default Settings**, **Quick Start** (random selection), or **Custom Selection** (by specific knowledge domains).
*   **Adaptive Navigation Control:** Supports backward-compatible forward-only or free-navigation mode (`BackNavigation` property).
*   **Keyboard Accessibility:** Full keyboard navigation (1-9 to select choices, Enter to submit/advance) and focus indicators.

### 🎯 Computer Adaptive Testing (CAT)
*   **CISSP-Style Difficulty Scaling:** Implements a 10-level difficulty scale (Fundamental to Insanely Hard) adapting to performance in real time.
*   **Sliding Window Algorithm:** Evaluates the last 3 questions to dynamically step difficulty up, down, or maintain.
*   **Smart Stopping Criteria:** Exam terminates dynamically upon mastery verification, early fail prediction, or maximum question cap.
*   **Topic Balancing:** Prioritizes under-represented domains in selection to ensure comprehensive coverage.

### 📊 Performance & Review Analytics
*   **Confidence Score:** Evaluates answering speed versus accuracy to calculate a test-taking confidence rating.
*   **Domain Analysis:** Immediate breakdown of performance sorted best-to-worst by knowledge domain.
*   **Targeted Review:** Filter and review correct, incorrect, or unanswered questions, including written rationales and explanations.

### 🔒 Security & Quality Hardening
*   **Strict Content Security Policy (CSP):** Header limits execution to `self` + `unsafe-inline` scripts and styles only.
*   **XSS Protection:** Direct DOM node creation (`textContent` and `createElement`) ensures absolute immunity to HTML injections.
*   **Data Integrity Check:** Schema validator checks default timers, question counts, and verifies that `AnswerKey` exactly matches choice options.
*   **Optimized Footprint:** Clean code with zero unused functions, variables, or polyfills (code reduced by >80%).

---

## 🛠️ How to Use

1.  **Download** [`exam.html`](./exam.html) and [`exam-builder.html`](./exam-builder.html).
2.  **Open** either file directly in any modern browser.
3.  **Load a JSON bank** by browsing a local file, inserting a URL, or testing the built-in **CISSP Demo Exam**.
4.  **Configure** your exam type and start taking questions.
5.  **Review** results, domain metrics, and detailed question explanations.

---

## 📂 Custom Exam Banks

Create, edit, and export custom test banks using the visual editor in **`exam-builder.html`**. 
For details on the underlying schema and fields, see the **[bank/README.md](./bank/README.md)** documentation.

---

## ⚖️ Disclaimer

**This software is 100% AI-generated.** While carefully structured, tested, and security-hardened, it is provided "as is" without warranty of any kind. Please refer to the in-app *Terms of Use* footer section for licenses, modifications, and usage policies.
