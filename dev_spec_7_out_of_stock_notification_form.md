# Out-of-stock notification form — dev spec
Site: allbirds.com · Priority 7 · High · Effort: Low (0.5-2 days)

## Problem
The product page for the Anytime Ankle Sock shows a 'Get Notified' CTA, which is a lead capture form for out-of-stock items, but the form lacks a trust layer (e.g., no mention of restock timing or privacy) and may be the highest drop-off point for interested buyers.

## Evidence (from the live site)
> The product page inventory shows a CTA 'Get Notified' and the body sample includes 'Get Notified' and 'Learn More'. The form likely collects email to notify when back in stock.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No visible trust elements near the CTA, such as 'We'll email you when it's back' or a privacy reassurance.

## Required change
h1: Anytime Ankle Sock; cta: Notify Me When Available; notes: Add microcopy: 'We'll email you as soon as it's back in stock. No spam.' Also consider a one-click email capture with a success message to reduce friction.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add microcopy: 'We'll email you as soon as it's back in stock. No spam.' Also consider a one-click email capture with a success message to reduce friction.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_out_of_stock_notification_form` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
