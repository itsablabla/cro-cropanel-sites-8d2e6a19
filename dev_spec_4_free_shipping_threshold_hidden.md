# Free shipping threshold hidden — dev spec
Site: allbirds.com · Priority 4 · High · Effort: Low (0.5-2 days)

## Problem
The homepage hero promotes 'Wildly Comfortable. Super Natural.' but does not mention the $100 free shipping threshold, which is only disclosed in the announcement bar and cart, creating an expectation gap for customers who may not meet the threshold.

## Evidence (from the live site)
> Homepage body sample includes 'Free ground shipping on orders over $100' in the announcement bar, but the hero section and CTAs ('SHOP MEN', 'SHOP WOMEN') do not mention this threshold. The cart drawer shows 'Spend more to earn free shipping! Shipping $5.00'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Hero lacks any mention of shipping costs or thresholds.

## Required change
h1: Wildly Comfortable. Super Natural. Free Shipping Over $100.; cta: SHOP MEN / SHOP WOMEN; notes: Add a subheading or badge to the hero that clearly states the free shipping threshold to set accurate expectations.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a subheading or badge to the hero that clearly states the free shipping threshold to set accurate expectations.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_free_shipping_threshold_hidden` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
