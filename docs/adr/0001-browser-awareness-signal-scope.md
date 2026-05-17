# Browser-awareness signal scope: a11y structure only, stripped at capture time

The browser-awareness **Evidence channel** could capture anywhere from URL-only to the full a11y tree including form values and body text. We're scoping v1 to URL + title + dwell + tab focus + **a11y structure** (roles, landmarks, headings, control labels, structure counts), with **a11y values** (form field contents, textarea/contenteditable text, body text inside paragraphs) dropped inside the renderer process before any data leaves it.

## Why

Structure is enough to classify into Work Profile Map bands when combined with Week 1 calibration interviews — it distinguishes "editing a CRM record" from "reading one", "drafting an email" from "triaging inbox", "filling an approval form" from "reviewing one". Values would add only marginal classification benefit while creating a regulatory cliff (GDPR Art. 88, ICO workplace-monitoring guidance, HIPAA exposure on healthcare tenants) and an audit surface Teho cannot defend at a works council.

Capture-time stripping — values dropped in the renderer, not server-side — is load-bearing for the public trust posture. "We never collect form values" is a statement a CISO can verify against an audited binary; "we filter them after collection" is not.

## Considered alternatives

- **URL + title only.** Cheaper and a simpler consent story, but can't disambiguate opaque-URL SPAs (Notion, Linear, modern Salesforce) and can't tell editing from reading. Rejected because the resulting Work Profile Map would have to lean too heavily on interviews to be defensible as "evidence-led".
- **A11y structure + values.** Best classification fidelity. Rejected on legal/consent grounds: captures salaries in HR, customer PII in CRMs, draft emails, search queries, password-manager autofills. Not viable in employment-monitoring jurisdictions.
- **Server-side value redaction.** Rejected because "we collected it, then deleted it" is not a defensible trust posture and creates breach exposure between capture and redaction.

## Consequences

- The renderer-side stripper is a critical-path security component — needs to be source-available, audited, and signed alongside the binary.
- Classification model must be trainable from structure + interviews alone; no fine-tuning on page content is possible.
- Forecloses any future "summarise this page" / "ask about this page" feature on this Evidence channel — that would require a separate consent flow and a separate channel.
- Chrome a11y tree shape is not a stable API; structure-extraction code needs telemetry for unrecognised shapes so breakage is visible.
