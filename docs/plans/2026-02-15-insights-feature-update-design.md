# Design: Update Marketing Site with Enhanced Insights Feature

**Date:** 2026-02-15
**Objective:** Update the expenlytics-website marketing materials to reflect the new LLM-powered financial intelligence insights that were added to the product since the site launched.

## Context

The expenlytics product has evolved significantly since the marketing site was last updated on Feb 8. The Insights feature has been completely redesigned from heuristic-based detection to full LLM-powered analysis with health scores, behavioral pattern detection, and narrative insights. The marketing site should reflect this current product state for new visitors.

## Changes Required

### 1. Update Feature Card (A)

**Location:** `src/pages/index.astro`, lines 146-154

**Current copy:**
```
Claude Haiku analyzes 6 months of data and generates observations about cross-category patterns, unusual spending, and actionable suggestions. Statistical trend detection too.
```

**New copy:**
```
Claude analyzes your spending and calculates a health score reflecting your savings rate and financial stability. Discovers behavioral patterns—grocery volatility, spending spikes, subscription creep—and delivers narrative insights ranked by severity. True LLM intelligence, not heuristics.
```

**Rationale:** The new copy emphasizes:
- Quantified metric (health score) - more compelling than generic "observations"
- Specific behavioral patterns instead of vague "cross-category patterns"
- Clear differentiation: LLM-powered vs. heuristic-based
- More sophisticated language that reflects the upgrade

### 2. Replace Insights Screenshot (C)

**Location:** `src/pages/index.astro`, lines 218-231 (detailed insights section)

**Current screenshot:** `/screenshots/insights.png`

**New screenshot:** To be captured from `http://localhost:3000/insights` showing:
- Health score (78) with narrative summary
- Key metrics cards (Savings Rate, Monthly Burn, Subscription Burden, etc.)
- Income vs Outflow chart
- Patterns grid with behavioral insights

**File to create:** `/public/screenshots/insights-enhanced.png`

**Rationale:** The new interface visually demonstrates the upgrade - shows the health score prominently, organized metrics, and specific patterns that users care about.

## Success Criteria

- Feature card copy emphasizes health score and behavioral pattern detection
- New screenshot displays the enhanced insights interface with health score prominent
- Copy accurately reflects the LLM-powered analysis capability
- No changelog-style listing - just highlighting what's genuinely new and valuable

## Implementation Notes

- Screenshot should be taken from running app at localhost:3000/insights
- Keep the minimal, data-dense aesthetic consistent with current marketing site
- The new copy should not feel like a list of features, but a compelling description of capability
