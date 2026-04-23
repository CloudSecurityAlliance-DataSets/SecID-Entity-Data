# SecID-Entity-Data

Raw content from well-known files at SecID entity domains. Part of the [SecID ecosystem](https://github.com/CloudSecurityAlliance/SecID).

## What This Contains

Cached copies of well-known files from organizations in the SecID entity registry:

- `llms.txt` / `llms-full.txt` — AI-friendly content descriptions ([llmstxt.org](https://llmstxt.org/))
- `robots.txt` — Crawling/scraping constraints
- `sitemap.xml` — Site structure
- `security.txt` / `.well-known/security.txt` — Vulnerability reporting contacts ([RFC 9116](https://www.rfc-editor.org/rfc/rfc9116))
- `.well-known/change-password` — Password change endpoint
- `.well-known/openid-configuration` — OpenID Connect discovery
- `skill.md` / `SKILL.MD` — AI agent skill definitions
- `humans.txt` — Human-readable credits

## Directory Structure

Files are stored using reverse-DNS directory structure, matching the SecID registry layout:

```
data/
├── com/
│   ├── cisco/
│   │   ├── llms.txt
│   │   ├── robots.txt
│   │   └── .well-known/
│   │       └── security.txt
│   ├── github/
│   │   ├── llms.txt
│   │   └── robots.txt
│   └── adobe/
│       └── llms.txt
├── org/
│   └── mozilla/
│       └── llms.txt
└── net/
    └── juniper/
        └── llms.txt
```

**Path algorithm:** Same as SecID registry — domain `cisco.com` becomes `com/cisco/`, domain `aws.amazon.com` becomes `com/amazon/aws/`.

## Relationship to SecID Registry

The **SecID entity registry** (`registry/entity/` in the [SecID repo](https://github.com/CloudSecurityAlliance/SecID)) records *which* well-known files an org has (presence/absence + status codes). This repo stores the *actual content* of those files.

| Concern | Where |
|---------|-------|
| "Does cisco.com have llms.txt?" | Entity registry `well_known` block |
| "What does cisco.com/llms.txt say?" | This repo: `data/com/cisco/llms.txt` |

## Freshness

Files are snapshots. Each fetch is recorded with a timestamp in the commit message. Content may be stale — always check the source URL for the latest version.

## License

Content in this repo is sourced from public URLs. Individual files retain their original licensing. The repository structure and tooling are [CC0 1.0](LICENSE).

## Related Repos

| Repo | Purpose |
|------|---------|
| [SecID](https://github.com/CloudSecurityAlliance/SecID) | Specification + registry data |
| [SecID-Service](https://github.com/CloudSecurityAlliance/SecID-Service) | Live resolver API + MCP server |
| [SecID-Server-API](https://github.com/CloudSecurityAlliance/SecID-Server-API) | Self-hosted resolver |
| [SecID-Client-SDK](https://github.com/CloudSecurityAlliance/SecID-Client-SDK) | Client libraries |
