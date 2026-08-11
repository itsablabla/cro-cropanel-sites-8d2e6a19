# Single-field email capture — dev spec
Site: allbirds.com · Priority 9 · High · Effort: High (5+ days)

## Problem
The homepage email signup form asks only for an email address, which is a low-friction but low-value capture that may attract low-intent subscribers and lacks a trust layer to justify the data request.

## Evidence (from the live site)
> The homepage form has 1 input, no labels, and a 'Sign Up' submit button. The body sample shows 'Subscribe to our emails Sign Up'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Sign Up; notes: Single email field with no label, no privacy note, no incentive beyond newsletter.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Get 10% Off Your First Order; notes: Add a clear value proposition (e.g., discount) and a microcopy trust line like 'No spam, unsubscribe anytime.' Consider adding a first name field only if it supports personalization, but keep it optional.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a clear value proposition (e.g., discount) and a microcopy trust line like 'No spam, unsubscribe anytime.' Consider adding a first name field only if it supports personalization, but keep it optional.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_field_email_capture` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
