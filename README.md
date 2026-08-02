# Bellwether Coffee

Bellwether Coffee is a Berkeley, California coffee-technology company founded in 2013 by Ricardo Lopez. It manufactures an all-electric, ventless, automatic commercial coffee roaster — the Shop Roaster (SCA Best New Product 2024) — and pairs it with a Green Coffee Marketplace, roast-automation and inventory software, retail packaging, and service.

- Website — https://bellwethercoffee.com
- Product — https://bellwethercoffee.com/shop-roaster
- Green Coffee Marketplace — https://bellwethercoffee.com/marketplace
- Help center — https://help.bellwethercoffee.com/
- Secondary-market listing — https://forgeglobal.com/bellwether-coffee_stock/

## API surface

**Bellwether Coffee publishes no public developer API.** Contract discovery on
2026-08-02 probed `bellwethercoffee.com`, `admin.bellwethercoffee.com`,
`api.bellwethercoffee.com` and `help.bellwethercoffee.com` for OpenAPI/Swagger,
GraphQL, MCP and A2A and found none. `api.bellwethercoffee.com` resolves to a
CloudFront distribution but fails TLS name validation and returns 502 — a private
origin behind the customer admin app, not a public API. `admin.bellwethercoffee.com`
is a single-page app that answers 200 with the same HTML shell for every path,
including `/.well-known/*`; those were rejected as false positives.

## What it does publish

A real machine-readable *web* surface, harvested verbatim:

| Artifact | Source | Notes |
|---|---|---|
| [`well-known/`](well-known/) | `/.well-known/api-catalog` | RFC 9727 linkset, `application/linkset+json` |
| [`well-known/bellwether-coffee-facts.json`](well-known/bellwether-coffee-facts.json) | `/facts.json` | Structured product, spec, pricing and economics facts |
| [`well-known/bellwether-coffee-robots.txt`](well-known/bellwether-coffee-robots.txt) | `/robots.txt` | Content Signals: `search=yes, ai-input=yes, ai-train=yes` |
| [`llms/`](llms/) | `/llms.txt` | 44 KB provider-published llms.txt |
| [`conformance/`](conformance/) | derived | Which standards apply, and which are N/A for a no-API provider |
| [`lifecycle/`](lifecycle/) | searched | Hardware generations, warranty, support — no API lifecycle |
| [`packages/`](packages/) | searched | No first-party SDK; registry search recorded |
| [`security/`](security/) | probed | TLS/HSTS/DNSSEC/CAA/SPF/DMARC posture |

That combination — api-catalog + facts.json + llms.txt + Content Signals — is
unusually complete for a hardware company with no API, and is the interesting
finding in this repo.
