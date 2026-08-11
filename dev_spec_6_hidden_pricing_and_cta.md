# Hidden pricing and CTA — dev spec
Site: allbirds.com · Priority 6 · Urgent · Effort: Medium (2-5 days)

## Problem
The product page for Anytime Ankle Sock lacks visible price and add-to-cart CTA in the extracted content, creating uncertainty and blocking purchase path.

## Evidence (from the live site)
> The page's CTAs include 'Get Notified' and 'Learn More' but no 'Add to Cart' or price appears in the extracted body sample; prices list only $5.00 (shipping) and $10 (likely other products).
> The inventory for '/products/anytime-ankle-sock' lists CTAs: 'Get Notified', 'Learn More', 'Sign Up', but no price is listed in the 'prices' array.
> CTAs include 'Get Notified' and 'Learn More' on the Anytime Ankle Sock product page, with no visible 'Add to Cart' or price in the extracted data.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified / Learn More; notes: No price or add-to-cart visible in the crawl; 'Get Notified' suggests out-of-stock or pre-order, but without price clarity users may abandon.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart (with price displayed); notes: Ensure price is prominently displayed and a clear add-to-cart CTA is available; if out of stock, show expected availability and price to manage expectations.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure price is prominently displayed and a clear add-to-cart CTA is available; if out of stock, show expected availability and price to manage expectations.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_hidden_pricing_and_cta` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
