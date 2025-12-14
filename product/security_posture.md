# Security Posture

This document defines what “security” means for MyPT.
It is intentionally practical and scoped to what a solo founder can credibly deliver.

This is **not a formal penetration test** or certification claim.

---

## Security Philosophy

- Prefer simple, inspectable systems over complex abstractions
- Minimize attack surface
- Keep data local by design
- Favor explicit allow-lists over implicit behavior
- Assume untrusted user input

---

## Data Flow Overview

- Inputs:
  - User prompts
  - Uploaded documents (workspace)
- Storage:
  - Local filesystem under controlled directories
  - RAG indexes stored locally
  - Optional logs (configurable)
- Processing:
  - Local embedding generation
  - Local retrieval
  - Local model inference
- Outputs:
  - Generated responses
- External connections:
  - None required for normal operation

---

## Deployment Hardening Measures

- Runs under a dedicated system user (not root)
- Restricted filesystem permissions for workspace and model files
- No execution of user-provided files
- No dynamic code execution based on prompts
- Network exposure limited to explicitly configured ports
- Default configuration suitable for local or reverse-proxied deployment

---

## Tooling & Agent Safety

- Tool execution is strictly allow-listed
- Tools are bound to explicit Python functions
- Tool arguments are validated
- No arbitrary shell or system access
- Model instructions alone cannot grant new capabilities

---

## LLM-Specific Considerations

- Prompt injection does not grant additional privileges
- The model cannot access environment variables or secrets
- Tool results are explicitly injected, not implicitly accessible
- History truncation prevents uncontrolled context growth

---

## Dependency & Supply Chain Hygiene

- Dependencies are pinned where possible
- Minimal dependency set preferred
- No external runtime downloads required
- Updates performed manually and deliberately

---

## What This Does NOT Claim

- No claim of formal certification (ISO, SOC2, etc.)
- No claim of zero vulnerabilities
- No claim of penetration-test-level assurance

For customers requiring deeper validation:

- Internal security review is supported
- External third-party audits can be engaged if required

---

## Security Positioning Summary

MyPT prioritizes **secure-by-design architecture and operational transparency** over compliance theater.
