# Naming

Names are built so Entra, Git, and the importer stay aligned.

## Conditional Access policies

```text
CA{NNN}-CSB-LVL{#}-{Persona}-{Category}-{AppsScope}-{Platform}-{Control}[-BLOCK]-v{major}.{minor}
```

| Part | Meaning | Example |
|------|---------|---------|
| `CA{NNN}` | Policy number / persona band | `CA000`, `CA101`, `CA500` |
| `CSB` | Cloud Shield Baseline | `CSB` |
| `LVL{#}` | Baseline level | `LVL1` … `LVL4` |
| Persona | Who it targets | `Global`, `Admins`, `Guests`, `ServiceAccounts`, `Agents`, `BreakTheGlass` |
| Category | Control family | `IdentityProtection`, `AttackSurfaceReduction`, … |
| Control | What it does | `StrengthMFA`, `DeviceCodeFlow`, … |
| `-BLOCK` | Grant control is block | optional |
| `-vX.Y` | Version | `-v1.0` |

**Rule:** `displayName` matches the filename without `.json`.

Example:

```text
CA000-CSB-LVL1-Global-IdentityProtection-AnyApp-AnyPlatform-StrengthMFA-v1.0
```

### Persona bands

| Range | Persona |
|-------|---------|
| 000–099 | Global |
| 100–199 | Admins |
| 200–299 | Guests |
| 300–399 | Service accounts |
| 400–499 | Agents |
| 500–599 | Break glass |

### Category tokens

| Token | Use |
|-------|-----|
| `IdentityProtection` | MFA, risk, session hardening |
| `AttackSurfaceReduction` | Blocks (country, apps, platforms, networks) |
| `BaseProtection` | Device join / compliance |
| `DataProtection` | App restrictions / app protection |

### Exceptions you will see

- **Agents** often omit `LVL#` today (`CA400-CSB-Agents-…`)  
- Some files use a `Catalog-` prefix (catalog / alternate copies)  
- A few policies are still on `v0.1` / `v0.9` while maturing  

## Groups

```text
SGU - CSB - CA###-… - Exclude
SGU - CSB - CA500-BreakGlassAccounts
SGU - CSB - CA300-ServiceAccounts
```

Exclude group names do **not** include the policy version suffix.

## Version bumps

When you change a policy:

1. Edit JSON under `Config/ConditionalAccess/`  
2. Bump `-v{major}.{minor}` in **filename** and `displayName`  
3. Leave exclude group names unchanged unless the logical policy identity changes  

Next: [Policies](policies.md) · [Deploy](deploy.md)
