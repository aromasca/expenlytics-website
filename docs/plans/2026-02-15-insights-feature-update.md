# Insights Feature Update Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Update the marketing website to showcase the new LLM-powered insights feature with health scores and behavioral pattern detection.

**Architecture:** Two simple changes to reflect product evolution: (1) Update the feature card copy in the Features section to emphasize health score and LLM analysis, (2) Replace the insights screenshot with a new one showing the enhanced interface with health score, metrics, and pattern detection.

**Tech Stack:** Astro static site, screenshot from running Next.js app

---

## Task 1: Save Enhanced Insights Screenshot

**Files:**
- Create: `/public/screenshots/insights-enhanced.png`

**Step 1: Capture screenshot from running app**

The screenshot has already been captured via Playwright. Copy it to the public directory.

**Step 2: Move screenshot to correct location**

Run:
```bash
cp insights-page.png /Users/aromasca/workspace/expenlytics-website/public/screenshots/insights-enhanced.png
```

Expected: File exists at `/public/screenshots/insights-enhanced.png`

**Step 3: Verify file exists and is readable**

Run:
```bash
ls -lh /Users/aromasca/workspace/expenlytics-website/public/screenshots/insights-enhanced.png
```

Expected: Shows file size > 100KB

**Step 4: Commit screenshot**

```bash
git add public/screenshots/insights-enhanced.png
git commit -m "chore: add enhanced insights screenshot with health score and patterns"
```

---

## Task 2: Update Feature Card Copy

**Files:**
- Modify: `src/pages/index.astro:146-154`

**Step 1: Read current content**

The current feature card is in the Features section, sixth card (AI Spending Insights).

Current HTML:
```html
<div class="rounded-xl border border-zinc-800 bg-zinc-900/50 p-6">
  <div class="mb-4 flex h-10 w-10 items-center justify-center rounded-lg bg-emerald-500/10">
    <svg class="h-5 w-5 text-emerald-400" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18"/></svg>
  </div>
  <h3 class="text-sm font-semibold mb-2">AI Spending Insights</h3>
  <p class="text-xs text-zinc-400 leading-relaxed">
    Claude Haiku analyzes 6 months of data and generates observations about cross-category patterns, unusual spending, and actionable suggestions. Statistical trend detection too.
  </p>
</div>
```

**Step 2: Replace the paragraph text**

Replace the `<p>` element with new copy:

```html
<p class="text-xs text-zinc-400 leading-relaxed">
  Claude analyzes your spending and calculates a health score reflecting your savings rate and financial stability. Discovers behavioral patterns—grocery volatility, spending spikes, subscription creep—and delivers narrative insights ranked by severity. True LLM intelligence, not heuristics.
</p>
```

**Step 3: Verify change looks correct**

Read lines 146-154 to confirm the paragraph text has been updated with new copy.

**Step 4: Commit copy update**

```bash
git add src/pages/index.astro
git commit -m "feat: update AI Spending Insights copy to emphasize health score and behavioral patterns"
```

---

## Task 3: Replace Insights Screenshot in Detail Section

**Files:**
- Modify: `src/pages/index.astro:218-231`

**Step 1: Read current insights section**

The detailed insights section has:
- Label: "INSIGHTS"
- Heading: "AI-powered spending analysis"
- Description paragraph
- Screenshot: `/screenshots/insights.png`

Current img tag (line 220):
```html
<img src="/screenshots/insights.png" alt="AI insights dashboard with spending observations and statistical analysis" class="w-full" />
```

**Step 2: Replace screenshot reference**

Change the img src to:
```html
<img src="/screenshots/insights-enhanced.png" alt="AI insights dashboard showing health score, spending metrics, and behavioral patterns" class="w-full" />
```

Also update the alt text to better describe the new visual.

**Step 3: Verify change looks correct**

Read lines 218-231 to confirm the screenshot reference has been updated.

**Step 4: Commit screenshot swap**

```bash
git add src/pages/index.astro
git commit -m "feat: replace insights screenshot with enhanced version showing health score and patterns"
```

---

## Task 4: Final Verification

**Step 1: Check all changes are present**

Run:
```bash
git diff HEAD~3
```

Expected: Shows three commits:
1. Added public/screenshots/insights-enhanced.png
2. Updated feature card copy in Features section
3. Replaced screenshot reference in detailed section

**Step 2: Build and verify no errors**

Run:
```bash
npm run build
```

Expected: Build completes successfully with no errors

**Step 3: Final commit summary**

Run:
```bash
git log --oneline -3
```

Expected: Shows three clean commits with clear messages about insights update

---

## Notes

- The new screenshot is significantly larger and more visually compelling than the old one
- Copy emphasizes "health score" and "behavioral patterns" which are the genuinely new capabilities
- Alt text updated to accurately describe what's now visible in the screenshot
- Changes are minimal and focused - no refactoring or scope creep
