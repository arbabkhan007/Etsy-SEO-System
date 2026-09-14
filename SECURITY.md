# Security Policy

## Supported Versions

Only the latest release is supported with security fixes.

| Version | Supported          |
| ------- | ------------------ |
| 2.1.x   | :white_check_mark: |
| < 2.1   | :x:                |

## Reporting a Vulnerability

**Please do not report security issues in public.** Do not open a GitHub issue,
pull request, or discussion for a vulnerability.

Instead, use one of these private channels:

1. **GitHub private vulnerability reporting** — go to the
   [Security tab](https://github.com/moiz-za/etsy-seller-seo-system/security/advisories/new)
   and click **Report a vulnerability**.
2. **Email** — `contact@moiz.solutions` with `SECURITY` in the subject line.

Please include:

- A description of the issue and its impact
- Steps to reproduce (or a proof of concept)
- Affected version / file / edition (skill vs. portable)
- Any suggested remediation, if you have one

You will receive an acknowledgement within **5 business days**. We will keep you
informed as we investigate and will credit you in the advisory unless you prefer
to stay anonymous. Please give us a reasonable window to ship a fix before any
public disclosure.

## Scope

This is a prompt/skill and documentation project. In scope:

- **Leaked secrets or private seller data** committed to the repository
  (shop IDs, API keys, personal paths, customer data)
- **Leak-guard bypass** — content that evades the CI/hook private-data scan
- **Prompt injection or unsafe instructions** in `skill/`, `portable/`, or
  `state-templates/` that could cause an AI tool to exfiltrate data, run
  destructive commands, or take unintended actions
- **Supply-chain risks** in `scripts/` or GitHub Actions workflows
- **Malicious pull requests** designed to introduce any of the above

## Out of Scope

- Etsy policy disputes, listing takedowns, or account issues
- SEO rankings, traffic, or sales outcomes
- Bugs in third-party AI tools (Claude, ChatGPT, Perplexity, Gemini) or in
  [SellWren](https://sellwren.com)
- General support questions — use
  [GitHub Discussions](https://github.com/moiz-za/etsy-seller-seo-system/discussions)

## Safe Harbor

We consider security research conducted in good faith, and consistent with this
policy, to be authorized. We will not pursue legal action against researchers
who report issues responsibly and avoid privacy violations, data destruction,
and service disruption.
