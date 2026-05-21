# Open Exam Application — Changelog

## Version 3.1 (Current)
**Files:** `exam.html` (436 lines), `exam-builder.html` (441 lines)
**Date:** 2026-05-20

**Summary:** Complete rewrite combining exam.html (v1.9.2) and exam-next.html (v2.0.1) into a unified, security-hardened application with ISC² CISSP theming, integrated CAT engine, dark mode, responsive mobile/tablet design, and zero dead code.

### Key Features & Enhancements

**1. Complete UI Rewrite**
- ISC² CISSP green/white color scheme
- Zero external dependencies — no CDN, no Google Fonts, fully offline
- Dark mode toggle with full dual-theme CSS variable system (persisted in localStorage)
- Mobile/tablet responsive with 3 breakpoints (768/600/374px)
- iOS Safari auto-zoom fix (16px inputs on mobile)
- Touch-safe hover effects via `@media(hover:hover)` — no sticky hover on touch devices
- WCAG-compliant 48px minimum tap targets for all interactive elements

**2. Computer Adaptive Testing (CAT) Integration**
- Ported from exam-next.html v2.0.1 with all bugs fixed
- 10-level difficulty scale: Fundamental → Insanely Hard
- Sliding window algorithm (3-question window) for adaptive difficulty adjustment
- Smart stopping criteria: early pass, early fail, mastery detection, max questions
- Domain balancing — prioritizes under-represented knowledge topics
- Real-time difficulty indicator with visual bar during exam
- CAT-specific results: pass/fail status, avg difficulty, highest level reached

**3. Security Hardening**
- Content Security Policy (CSP) meta header — `self` + `unsafe-inline` only
- XSS-safe DOM: all user data inserted via textContent/createTextNode — zero innerHTML injection
- URL sanitization: protocol validation (http/https only), localhost blocking
- Data integrity layer: JSON schema validation, AnswerKey ∈ Choices verification, duplicate question detection
- External links secured with `rel="noopener noreferrer"`

**4. Bug Fixes (12+ from v1.9.2/v2.0.1 audit)**
- Fixed: choices displayed below navigation buttons (layout bug)
- Fixed: CSS class name collision (`.fb` defined twice with conflicting meanings)
- Fixed: meaningless ternary `isCorrect ? 0 : 0` in confidence score calculation
- Fixed: dropdown fallback failure when question pool < 5
- Fixed: goBack() time accumulation inconsistent with goNext()
- Fixed: loadNewBank() did not reset timer display
- Fixed: restartExam() always called normal mode, ignored CAT state
- Fixed: loadNewBank() did not reset CAT state variables
- Fixed: onExamDataLoaded() missing default settings info in normal mode
- Fixed: CAT unanswered questions incorrectly counted as "wrong" instead of "unanswered"
- Fixed: double-submit possible without guard
- Fixed: CSS.escape polyfill overwrote entire CSS object

**5. Mobile File Input Fix**
- Replaced `<button onclick="el.click()">` with `<label for="file-input">` pattern
- File input uses visually-hidden approach (`position:absolute;opacity:0`) instead of `display:none`
- Works reliably on all mobile browsers including iOS Safari where programmatic `.click()` on hidden file inputs is blocked

**6. User Experience Enhancements**
- Global error handler: catches runtime errors, async promise rejections, and manual errors with visual toast (auto-dismiss 8s)
- Keyboard shortcuts: number keys 1-9 select choices, Enter advances/submits
- Page close guard (beforeunload) during active exam session
- Accessible focus rings (:focus-visible) for keyboard navigation
- Print-friendly results page (Ctrl+P hides all UI except score)
- Terms of Use (7 sections) and Version History integrated into app footer

**7. Dead Code Cleanup**
- Removed unused `Sec.esc()` function (replaced by textContent pattern throughout)
- Removed unused CSS.escape polyfill (inherited from v1.9.2, no longer called)
- Removed unused CSS class `.f9` (font-weight:900, never referenced in HTML)
- All CSS classes, JS functions, and variables verified in-use via automated audit

**8. Exam Builder v3.1 — Complete Redesign**
- All innerHTML XSS vulnerabilities fixed (textContent + createElement throughout)
- Inline event handler injection fixed (addEventListener replaces inline handlers)
- New sectioned sidebar layout: Settings and Questions in clearly separated sections with border dividers
- Proper form spacing: 12px between groups, consistent label sizing (11px uppercase)
- Editor area: card with shadow, max-width 720px, clear header with border separator
- Button sizing system: btn-p (primary), btn-sm (small), btn-xs (extra small), btn-icon (28x28)
- Domain percentages in highlighted box with live total % indicator
- Mobile-safe file import: `<label for="">` pattern matching exam app
- Dark mode toggle with matching theme system
- iOS Safari zoom fix (16px inputs)
- Responsive: 3 breakpoints (900px sidebar shrink, 768px single-column, 480px compact)

**9. Performance**
- DocumentFragment batch DOM rendering for choices, questions, domain bars, and review items
- Debounced setup UI updates (80ms) for domain checkbox changes
- IIFE module pattern — all app state encapsulated, zero global scope pollution

---

## Version 2.0.1 (Superseded)
**File:** `exam-next.html`
**Date:** 2025-04-19

1. Bug fix: submit button re-enabled on restart
2. Exam builder: removed external Google Font dependencies

## Version 2.0.0 (Superseded)
**File:** `exam-next.html`

1. Computerized Adaptive Testing (CAT) engine
2. Sliding window algorithm for adaptive difficulty
3. Domain balancing, advanced stopping criteria
4. Inherited 30+ bug fixes from v1.9.1

## Version 1.9.2 (Superseded)
**File:** `exam.html`
**Date:** 2025-04-19

1. Bug fix: submit button re-enabled on restart

## Version 1.9.1 (Superseded)
**File:** `exam.html`

1. 30+ bug fixes by bank4500 (Aj. Bank)
2. Strict JSON validation, math fixes, UI/security improvements
3. XSS-safe DOM construction, timer memory leak fix
4. CSS.escape polyfill fix (subsequently removed in v3.1 as unnecessary)

## Version 1.9.0

1. UI overhaul with purple gradient theme
2. Card-based layout, enhanced buttons and inputs
3. Mobile responsive design
4. Performance badges on results screen

## Version 1.8.5

1. Terms of Use section added
2. Disclaimer box on initial page

## Version 1.8.4

1. Confidence Score system
2. Per-question time tracking
3. Time warning feature
4. Unanswered question tracking and review

## Version 1.7.0

1. Proportional distribution algorithm (Largest Remainder Method)
2. Debug mode for developers
3. Fixed custom question count input bug

## Version 1.6.0

1. Three exam setup modes (Default, Quick Start, Custom Domain)
2. Mobile responsive design
3. Sorted domain results

## Version 1.5.0

1. Flexible exam setup options
2. Custom file input UI
3. Progress bar based on question position
4. BackNavigation JSON field support
5. Version display
