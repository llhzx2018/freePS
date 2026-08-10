# VF Infra Phase 3 Live Provider Secret Contract

This file belongs only to the isolated `vf-infra-phase3-live` CI branch. It contains no secret values.

Required GitHub Actions repository secrets for the live provider gate:

- `VF_INFRA_DYNADOT_KEY` — optional live Dynadot API key. Prefer source-IP restriction when the execution environment has a fixed egress IP.
- `VF_INFRA_DYNADOT_SANDBOX_KEY` — Dynadot Sandbox API key; preferred for non-production write-capable credentials.
- `VF_INFRA_CLOUDFLARE_TOKEN_A` — minimum read token able to list Zones.
- `VF_INFRA_CLOUDFLARE_TOKEN_B` — second independent Cloudflare account token, used only for same-provider account isolation validation.
- `VF_INFRA_LINODE_TOKEN` — Personal Access Token with read-only account and Linode instance scopes.
- `VF_INFRA_VULTR_KEY` — dedicated low-privilege service-user API key; use Vultr API IP Access Control where practical.

Rules:

1. Never commit secret values to Git, FULL, ZIP, issue, PR, artifact, logs, or chat.
2. The workflow prints only secret-presence booleans, sanitized counts/status codes, and one-way account anchors.
3. The live gate performs read-only account/inventory requests only. No DNS modification, renewal, VPS power action, creation, deletion, SSH, or payment action is implemented.
4. Missing secrets remain `BLOCK_NO_SECRET`; they are not converted to PASS.
5. After the live evidence is collected and Phase 3 is sealed, the isolated branch should be removed/reset so the test harness does not become part of the product source tree.
