---
name: launch-readiness
description: Audit a product before launch day. Checks the buy path end to end, the product page, the download, refunds, analytics and the announcement plan, and returns a go/no-go list with the fix for each blocker. Use when someone says "we launch tomorrow", "is this ready", or before announcing anything publicly.
---
# Launch readiness audit

## When to use
Before any public announcement of a product, price change or new version. Run it again the morning of
the launch; things break overnight (expired links, unpublished drafts, wrong prices).

## Inputs
- The product page URL or its source files, and the checkout/download URL.
- The price and any discount codes.
- Where the launch will be announced (list of channels).
- Optional: the refund policy, the receipt/thank-you email text, the analytics setup.

## Steps
1. **Walk the buy path as a stranger.** Landing page → buy button → checkout → receipt → download →
   first-use instructions. Note every click. Every buy button on every page must point to the same live
   checkout. Flag any `#`, empty or draft links.
2. **Check the offer matches everywhere.** Price, discount code, what's included and the refund window
   must say the same thing on the page, the checkout, the listing and the announcement drafts.
3. **Open the deliverable.** Unzip or open it. Does it contain what the page promises? Is there a
   README or "start here"? Does the first command in the instructions actually work?
4. **Check trust signals are honest.** No invented numbers, reviews or logos. Claims are specific and
   checkable. There's a way to contact a human.
5. **Check the basics.** HTTPS, mobile layout (375px wide), page title and meta description, a social
   preview image, a 404 page, spelling of the product name.
6. **Check you can measure it.** Can you tell tomorrow how many people visited, clicked buy and bought?
   If not, note the cheapest way to find out (checkout dashboard, server logs, UTM tags).
7. **Check the announcement plan.** Each channel's rules allow the post; drafts exist; someone will be
   around to reply for the first hours.
8. Classify every finding as **BLOCKER** (launch would lose money or trust), **FIX SOON** or **NICE**.

## Output format
```
VERDICT: GO | NO-GO (n blockers)

BLOCKERS
1. <what's wrong> → <exact fix> (where)

FIX SOON
...

NICE
...

VERIFIED OK
- <thing checked>: <how you checked it>
```

## Rules
- Only mark something OK if you actually checked it. "Looks fine" isn't a check.
- Prefer the smallest fix that removes a blocker today over a redesign.

## Worked example
**Input:** "We launch the Tidy Desk Notion templates tomorrow on Gumroad, $12, code EARLY for $4 off.
Page: tidydesk.example.com. Announcing on our newsletter and r/Notion."

**Output:**
```
VERDICT: NO-GO (2 blockers)

BLOCKERS
1. The hero "Buy now" button links to https://gumroad.com/l/tidy-desk-draft, which shows "This product
   is not published". → Publish the Gumroad product, then replace the link on the page with
   https://tidydesk.gumroad.com/l/desk (both buttons: hero and footer).
2. The page says "code EARLY: 50% off" but the Gumroad code is $4 off $12 (33%). → Change the page copy
   to "$8 with code EARLY until 10 Oct", or change the code to 50%. The newsletter draft repeats the 50%
   claim, so fix it there too.

FIX SOON
1. The zip contains 6 templates; the page says "7 templates". Either add the missing "Weekly review"
   template or change the page to 6.
2. No meta description. Suggested: "Seven Notion templates for a calmer work week: planner, CRM,
   reading list and more. $12, one-time."
3. r/Notion allows self-promotion only in the weekly thread; the draft is a standalone post. Move it to
   the Thursday thread.

NICE
1. The social preview image is the default Gumroad one. A 1200×630 screenshot of the planner would do
   better when shared.

VERIFIED OK
- HTTPS: page loads on https with a valid certificate.
- Mobile: checked at 375px, no horizontal scroll, buy button visible without scrolling.
- Receipt email: sent a $0 test purchase; the receipt links to the download.
- Refund policy: "14 days, no questions" appears on the page and in the Gumroad settings.
```
