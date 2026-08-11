# Competing hero CTAs — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
The hero presents two equally prominent CTAs (SHOP MEN and SHOP WOMEN) that split user intent and delay the path to a single product category.

## Evidence (from the live site)
> Hero section contains both 'SHOP MEN' and 'SHOP WOMEN' CTAs, with no primary/secondary visual hierarchy in the extracted copy.
> H1: 'Wildly Comfortable. Super Natural.' with CTAs 'SHOP MEN' and 'SHOP WOMEN' but no subheadline to clarify the brand's specific benefits.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Two CTAs of equal weight force an immediate gender choice, adding friction for users who may not have a preference or are browsing for gifts.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All (primary) with secondary 'Shop Men' / 'Shop Women' links; notes: A single primary CTA to 'Shop All' reduces decision load and lets users self-segment later, improving flow to product discovery.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN A single primary CTA to 'Shop All' reduces decision load and lets users self-segment later, improving flow to product discovery.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_hero_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
