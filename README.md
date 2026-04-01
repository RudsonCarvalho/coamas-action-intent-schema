# COA-MAS Action Intent Schema

Canonical JSON Schema (draft/2020-12) for the **Action Intent** — the universal cross-domain artifact of the COA-MAS governance meta-framework.

## What is the Action Intent?

The Action Intent is the "passport" of the COA-MAS federation. It is a standardized, cryptographically signed declaration of:

- **Who** is acting (agent identity, delegation chain, GOV-RISK attestation)
- **What** they intend to do (tool URI, operation type, resource scope)
- **What effect** they declare it will produce (reversibility, estimated scope, data sensitivity)
- **Cryptographic binding** (ephemeral DPoP public key for proof-of-possession)

Any receiving domain can read it. Each domain evaluates it by its own sovereign criteria using its own GOV-RISK. Domain A's internal policy, prompts, and risk weights are never transmitted — only the declared intent, authenticated by Domain A's governance layer.

## Files

| File | Description |
|------|-------------|
| `schema/action_intent_v1.0.0.json` | Canonical JSON Schema v1.0.0 |

## Citing This Schema

If you use this schema in your work, please cite the Zenodo record:

```
Carvalho, R.K.S. (2026). COA-MAS Action Intent Schema v1.0.0.
Zenodo. doi.org/10.5281/zenodo.19376419
```

📄 **Zenodo record:** https://zenodo.org/records/19376420

## Related Publications

**COA-MAS v2 — A Meta-Framework for Cross-Domain Multi-Agent Governance**  
Working Paper v0.3 — this schema is a supplementary artifact  
→ [doi.org/10.5281/zenodo.19376738](https://zenodo.org/records/19376739)

**COA-MAS v1 — Cognitive Organization Architecture for Multi-Agent Systems**  
→ [doi.org/10.5281/zenodo.19057202](https://doi.org/10.5281/zenodo.19057202)

## How It Works

```
Domain A                          Domain B
─────────────────────────────     ─────────────────────────────
GOV-RISK-A signs Action Intent    GOV-RISK-B evaluates intent
     │                                 using its own Executable
     │  POST /gov-risk/authorize        Culture (sovereign)
     ├────────────────────────►        │
     │                                 ▼
     │◄────────────────────────   Issues Action Claim (V1 schema)
     │  Action Claim (signed      with cnf (DPoP key binding)
     │  by GOV-RISK-B)
     │
     ▼
AASG-B validates locally-signed
Action Claim + DPoP proof
Zero cognitive load at runtime
```

## Federation Modes

The Action Intent is the universal artifact consumed by all COA-MAS federation modes:

| Mode | Name | When to use |
|------|------|-------------|
| 0 | Intra-Domain (COA-MAS V1) | Same domain — deterministic, microsecond latency |
| 1 | Sovereign Visa | Medium-high trust, direct tool execution |
| 2 | Ambassador | Low/zero trust, maximum isolation |
| 3 | Clearinghouse | Regulated industries with neutral hub |
| 4 | ZK-Policy *(future)* | Full policy confidentiality via ZKML |

## Schema Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0.0 | 2026-03-31 | Initial release |

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — Rudson Kiyoshi Souza Carvalho
