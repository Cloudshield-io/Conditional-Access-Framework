# CloudShield Conditional Access Baseline

A Microsoft Entra Conditional Access baseline as code. Policies, groups, and named locations live under [`Config/`](Config/) so you can version, review, and deploy the same guardrails across tenants.

The baseline is organized by **personas** (who a policy protects) and **levels** (recommended rollout order). Inspired by [j0eyv/ConditionalAccessBaseline](https://github.com/j0eyv/ConditionalAccessBaseline) and Microsoft Conditional Access for Zero Trust guidance.

> [!IMPORTANT]
> Add emergency access accounts to **`SGU - CSB - CA500-BreakGlassAccounts`** before enabling policies.

## Start here

| Step | What to do |
|-----:|------------|
| 1 | Learn **personas** — who each policy band covers (see below) |
| 2 | Pick a starting **level** — Level 1 for every tenant (see below) |
| 3 | Follow **Deploy this baseline** — import, report-only, analyze, then activate |

## Personas at a glance

Personas answer **who** a policy protects. The number is a band in the policy name (`CA000`, `CA100`, …). Global is the floor everyone meets; other personas add stricter rules. Break glass accounts are excluded from most policies so emergency access still works.

| Band | Persona | Role |
|------|---------|------|
| 000 | Global | Catch-all bare minimum for everyone; exclusions rare and deliberate |
| 100 | Admins | Privileged roles; stronger MFA and tighter sessions than Global |
| 200 | Guests | External users; limit apps and session lifetime |
| 300 | Service accounts | Automation in a dedicated group; MFA + trusted locations |
| 400 | Agents | Agent identities and users; restrictive by default |
| 500 | Break glass | Emergency accounts only; usable in a crisis, tightly controlled |

## Levels at a glance

Levels are a **recommended rollout order** — our opinion on what to enable first — not a hard security standard. Policy names use `LVL1`–`LVL4` so you can filter in Entra and Git.

| Level | Meaning |
|------:|---------|
| **1** | Floor for every tenant — whether you have 5 or 5,000 people |
| **2** | Harden security with low impact on standard employees |
| **3** | Critical identities are covered; tighten users and devices next |
| **4** | Prefer security over short workability hits |
| **5** | Maximum foundation for large or high-assurance orgs — no `LVL5` policies in Config yet |

Agents (CA400–404) have no `LVL#` tag today. Enable them when those workloads exist — usually after Level 2 or 3.

## Deploy this baseline

1. Turn off **Security Defaults** (they conflict with Conditional Access).  
2. Confirm built-in **MFA** and **phishing-resistant MFA** authentication strengths exist.  
3. **Import** the baseline in **Off** or **Report-only** state using one of these tools:

| Tool | Link |
|------|------|
| **CA Importer** | [ca-importer.mikkeldamgaard.dk](https://ca-importer.mikkeldamgaard.dk) |
| **IntuneManagement** | [Micke-K/IntuneManagement](https://github.com/Micke-K/IntuneManagement) |

4. Create **break-glass** accounts (or reuse existing ones) and add them to `SGU - CSB - CA500-BreakGlassAccounts`.  
5. Add automation / service accounts to `SGU - CSB - CA300-ServiceAccounts` if you use that persona.  
6. Set the Conditional Access policies you want to use to **Report-only**. Leave them there for **at least one month** before activating. Start with **Level 1**, then advance level by level.  
7. **Analyze** policy impact in Microsoft Entra ID (sign-in logs / What If / insights).  
8. **Activate** the policies (On) when the impact looks acceptable.

More detail if you need it: [docs/deploy.md](docs/deploy.md).

## Optional deeper docs

The sections above are enough to get started. Use these only when you need more detail.

| Doc | Description |
|-----|-------------|
| [Personas](docs/personas.md) | Who each band protects (000–500) |
| [Levels](docs/levels.md) | Where to start (1 → 5) |
| [Policies](docs/policies.md) | Catalog by level and persona |
| [Deploy](docs/deploy.md) | Full deploy order: import, report-only, analyze, activate |
| [Exclusions](docs/exclusions.md) | Break glass and per-policy excludes |
| [Named locations](docs/named-locations.md) | Country / compliant-network lists |
| [Naming](docs/naming.md) | `CSB`, `LVL#`, versioning |

## Authors

### Philip Ølholm Fredberg Hassing
Cloud Security Consultant  
[GitHub](https://github.com/CloudShieldio) · [LinkedIn](https://www.linkedin.com/in/philip-fredberg-hassing/)

### Mikkel Lyngskov Damgaard
Junior Cloud Infrastructure Consultant  
[GitHub](https://github.com/MrMikkelll) · [LinkedIn](https://www.linkedin.com/in/mikkel-damgaard/)

## License

MIT — see [LICENSE](LICENSE).
