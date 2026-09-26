---
name: support-reply
description: Draft a support reply that solves the customer's problem in one message, covering how-to, bug, refund, billing and angry emails, following your stated policies, with a clear next step and a note of what to fix so it doesn't recur. Use when answering customer emails, DMs or tickets.
allowed-tools: Read, Grep, Glob
---
# Support reply

## When to use
Any customer message that needs an answer. Especially useful for refunds and upset customers, where
tone matters most.

## Inputs
- The customer's message (and earlier thread if any).
- Your policies: refunds, licence, response times, what you can and can't do.
- Optional: product docs or repo to search for the answer, the customer's order details.

## Steps
1. **Classify:** how-to · bug · refund/billing · feature request · complaint · other. Note the one
   thing they actually need.
2. **Find the answer.** Search the docs/repo. If you can't confirm it, say what you'll check, not a guess.
3. **Draft**, in this order:
   - First line: the answer or the action you've taken ("I've refunded your order").
   - Steps if needed, numbered, copy-pasteable.
   - One line of acknowledgement if they're frustrated. Sincere, not grovelling.
   - The next step and when ("If step 2 fails, reply with the error text and I'll look today").
4. **Policy:** apply it as written. If the policy says yes, say yes without making them argue. If it
   says no, explain once, offer the best alternative, and don't hide behind "policy".
5. **Internal note:** what should change so this question stops arriving (doc fix, bug ticket, FAQ).

## Output format
```
TYPE: ...   NEEDS: ...
REPLY:
<ready to send>
INTERNAL: <doc/bug/FAQ action>
```

## Rules
- Never promise dates or features you can't commit to.
- Never blame the customer. "The instructions weren't clear" beats "you missed step 3".
- Keep it under 150 words unless steps require more.

## Worked example
**Input:** "I bought the kit yesterday and the workflow fails with 'Could not fetch an OIDC token'. This is
useless. I want a refund." Policy: refunds within 14 days, no questions asked.

**Output:**
```
TYPE: bug/setup + refund   NEEDS: working setup, or their money back

REPLY:
Hi Sam, sorry about that. I've started your refund just in case; it'll show in 5–10 days, and you
can keep the files.

That error has a quick fix if you'd like to keep going. The workflow needs permission to request a
token. Add this under the job in .github/workflows/standup.yml:

    permissions:
      contents: write
      id-token: write

Then re-run it from the Actions tab. If it still fails, reply with the new error line and I'll look
at it today.

INTERNAL: the setup guide doesn't mention id-token: write. Add it to the guide's workflow snippet and
the troubleshooting section, and have setup check for it.
```
