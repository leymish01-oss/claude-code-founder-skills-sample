# Claude Code skills for founders (free sample)

Three Claude Code skills for the non-coding work of running a small product business, taken unchanged
from the 25-skill [Claude Code Skills Pack](https://www.leymish.com/products/skills-pack.html).

| Skill | What it does |
|---|---|
| `launch-readiness` | Audits a product before launch day: walks the buy path, checks the offer matches everywhere, opens the download, and returns a go/no-go list with the fix for each blocker. |
| `pricing-experiment` | Designs a pricing test from your real numbers: hypothesis, revenue per visitor as the metric, the sample you'd need, stop rules and a decision rule written before you start. |
| `support-reply` | Drafts a support reply that solves the problem in one message, follows your refund policy as written, and notes what to fix so the question stops arriving. |

Each `SKILL.md` has a trigger description (so Claude loads it when relevant), inputs, steps, an output
format, rules, and a **worked example** with a realistic input and the complete output.

## Install

Copy the folders in `skills/` into `~/.claude/skills/` (every project) or `<your-project>/.claude/skills/`
(one project), then start a new Claude Code session:

```bash
git clone https://github.com/leymish01-oss/claude-code-founder-skills-sample
cp -r claude-code-founder-skills-sample/skills/* ~/.claude/skills/
```

Then just ask: "check whether my product page is ready to launch tomorrow".

## The other 22

The full pack adds landing-page-critique, product-listing, changelog-writer, seo-article,
keyword-brief, devto-crosspost, build-in-public-post, case-study, bug-triage, feedback-synthesis,
faq-builder, onboarding-emails, competitor-teardown, partner-research, community-post,
directory-submissions, readme-writer, weekly-review, sales-reconcile, decision-log,
experiment-postmortem and release-announcement, plus an installer.

- [Claude Code Skills Pack](https://www.leymish.com/products/skills-pack.html): $15
- [Bundle with the Autonomous Company Kit](https://www.leymish.com/products/bundle.html): the agent team
  that runs [LeyMish Labs](https://www.leymish.com) in public, plus all 25 skills

## Licence

These three skills are MIT (see `LICENSE`). The full pack has its own licence.
