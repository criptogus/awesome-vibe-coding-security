# Awesome Vibe Coding Security

A short, maintained list of free tools and references for founders and small teams shipping apps built with Lovable, Cursor, Bolt, Replit or Codex. Each entry is something you can use before launch without a security team.

Curated by Liquid Cybersecurity (https://liquidplatform.org). Reviewed monthly. Last review: 2026-11-23. Inclusion is not an endorsement, and no tool on this list proves an app is secure.

## Contents

- [Secrets and keys](#secrets-and-keys)
- [Database access (Supabase and Firebase)](#database-access-supabase-and-firebase)
- [Dependencies](#dependencies)
- [Code patterns](#code-patterns)
- [Live site: headers, TLS and email](#live-site-headers-tls-and-email)
- [Payments and webhooks](#payments-and-webhooks)
- [AI features](#ai-features)
- [Checklists and standards](#checklists-and-standards)
- [Pre-launch kits](#pre-launch-kits)

## Secrets and keys

- [Gitleaks](https://github.com/gitleaks/gitleaks) - Finds API keys and tokens committed to a Git repository, including old commits.
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - Secret scanner that can check whether a found key is still valid.
- [GitHub secret scanning and push protection](https://docs.github.com/en/code-security/secret-scanning) - Blocks known key formats before they reach the repository.
- Rule of thumb: anything with a `VITE_`, `NEXT_PUBLIC_` or `EXPO_PUBLIC_` prefix ships to every visitor. Only publishable keys belong there.

## Database access (Supabase and Firebase)

- [Supabase Row Level Security guide](https://supabase.com/docs/guides/database/postgres/row-level-security) - How to tie each row to the signed-in user.
- [Supabase Security Advisor](https://supabase.com/docs/guides/database/database-advisors) - Built-in linter that flags tables without RLS and risky functions.
- [Firebase Security Rules](https://firebase.google.com/docs/rules) - The equivalent control for Firestore and Storage.

## Dependencies

- [OSV-Scanner](https://github.com/google/osv-scanner) - Checks lockfiles against the open OSV vulnerability database.
- [npm audit](https://docs.npmjs.com/cli/commands/npm-audit) - Built into npm; start with `npm audit --omit=dev`.
- [Dependabot](https://docs.github.com/en/code-security/dependabot) - Opens pull requests when a dependency has a known fix.

## Code patterns

- [Semgrep](https://github.com/semgrep/semgrep) - Open-source rules for common web mistakes in JavaScript, TypeScript and Python.
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/) - Short, practical fixes per topic (authentication, XSS, file upload).

## Live site: headers, TLS and email

- [Mozilla HTTP Observatory](https://developer.mozilla.org/en-US/observatory) - Grades security headers on a public URL.
- [CSP Evaluator](https://csp-evaluator.withgoogle.com/) - Explains weaknesses in a Content-Security-Policy.
- [SSL Labs Server Test](https://www.ssllabs.com/ssltest/) - Checks the TLS configuration of a domain.
- [Liquid domain check](https://liquidplatform.org/domain-check) - Free SPF and DMARC check for a domain.

## Payments and webhooks

- [Stripe webhook signature verification](https://docs.stripe.com/webhooks#verify-events) - Every webhook should verify the provider signature.
- Rule of thumb: prices and plan changes are decided on the server, never taken from the browser.

## AI features

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/) - Prompt injection, excessive agency, unbounded consumption and more.
- Rule of thumb: if user text reaches a model that can send email, write data or call tools, add per-user limits, a spending cap and server-side checks on what the output can do.

## Checklists and standards

- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/) - The reference list of what a web app should verify.
- [OWASP Top 10](https://owasp.org/Top10/) - The most common web application risks.
- [Vibe coding security checklist before launch](https://liquidplatform.org/guides/vibe-coding-security-checklist-before-launch) - A plain-language checklist for AI-built apps.

## Pre-launch kits

- [Liquid pre-launch check](https://liquidplatform.org/guides/vibe-coding-security-checklist-before-launch) - Free, read-only agent skill and zero-dependency script (MIT) that flags common launch mistakes in a repository. Findings are leads to review; no finding does not mean the app is safe.

## Contributing

Open a pull request or an issue. Suggest a free tool or reference that helps small teams ship AI-built apps more safely. Entries must be maintained, free to use, and described without claims of guaranteed security.
