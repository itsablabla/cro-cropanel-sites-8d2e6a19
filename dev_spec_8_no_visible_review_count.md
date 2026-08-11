# No visible review count — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The product page shows a reviews section but no aggregate rating or count near the price, so shoppers cannot quickly gauge social proof at the point of purchase.

## Evidence (from the live site)
> H2 'Reviews for Anytime Ankle Sock' exists, but no star rating or review count appears in the body sample or CTAs; the page has a 'Get Notified' CTA indicating out-of-stock, but no trust signal.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: Reviews section present but no aggregate rating or count visible near the product title/price.

## Required change
h1: Anytime Ankle Sock; cta: Get Notified; notes: Add a star rating and review count (e.g., '★★★★★ 1,200 reviews') directly under the product title.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a star rating and review count (e.g., '★★★★★ 1,200 reviews') directly under the product title.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_visible_review_count` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
