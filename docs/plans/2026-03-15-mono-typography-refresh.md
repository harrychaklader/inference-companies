# Mono Typography Refresh Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Refresh the site typography so the entire page uses one stronger mono font with clearer hierarchy and spacing.

**Architecture:** Keep the static single-file HTML structure intact. Add a lightweight Python verification script that enforces the mono-font contract and a few key typography rules, then update the CSS in `index.html` to satisfy that contract.

**Tech Stack:** HTML, inline CSS, vanilla JavaScript, Python via `uv`

---

### Task 1: Add typography regression coverage

**Files:**
- Create: `tests/verify_typography.py`
- Test: `tests/verify_typography.py`

**Step 1: Write the failing test**

Create a Python script that reads `index.html` and asserts:

- the Google Fonts import includes `Azeret Mono`
- there is only one imported font family
- `:root` defines `--font-mono`
- every explicit `font-family` declaration uses `var(--font-mono)` or the `--font-mono` token definition
- the `h1`, `.subtitle`, and `th` rules contain the refreshed hierarchy properties

**Step 2: Run test to verify it fails**

Run: `uv run python tests/verify_typography.py`
Expected: FAIL because `index.html` still imports `IBM Plex Mono` and lacks the new hierarchy rules.

**Step 3: Commit**

```bash
git add tests/verify_typography.py
git commit -m "Add typography regression script. gpt-5. 03-15-2026."
```

### Task 2: Refresh mono typography styles

**Files:**
- Modify: `index.html`
- Test: `tests/verify_typography.py`

**Step 1: Write minimal implementation**

Update `index.html` to:

- replace the font import with `Azeret Mono`
- rename the shared font token to `--font-mono`
- tighten hero title sizing and tracking
- improve subtitle rhythm and max width
- strengthen chip and table-header typography
- add numeric presentation details such as tabular lining figures
- keep responsive behavior intact with matching mobile type adjustments

**Step 2: Run test to verify it passes**

Run: `uv run python tests/verify_typography.py`
Expected: PASS

**Step 3: Review the page manually**

Open `index.html` locally and confirm the hero, chips, headers, and table rows all reflect the same mono family with clearer hierarchy.

**Step 4: Commit**

```bash
git add index.html tests/verify_typography.py docs/plans/2026-03-15-mono-typography-refresh-design.md docs/plans/2026-03-15-mono-typography-refresh.md
git commit -m "Refresh mono typography across the page. gpt-5. 03-15-2026."
```

### Task 3: Final verification and push

**Files:**
- Verify: `index.html`
- Verify: `tests/verify_typography.py`

**Step 1: Run final verification**

Run: `uv run python tests/verify_typography.py`
Expected: PASS

**Step 2: Check git state**

Run: `git status --short --branch`
Expected: clean working tree on `master`

**Step 3: Push**

Run: `git push origin master`
Expected: remote update succeeds
