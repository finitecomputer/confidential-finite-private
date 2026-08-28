# confidential-finite-private

Measured Tinfoil deployment configuration for Finite Private inference.

The outer deployment identity is model-independent: `finite-private`. The
served model identity is pinned separately in `tinfoil-config.yml`; the first
release candidate serves `glm-5-3-flash` from the exact Hugging Face revision
recorded there.

This satellite contains only the reviewed deployment manifest and the release
workflows that measure and publish it. Source code and the production cutover
runbook live in `finitecomputer/finite-mono`.

Required Tinfoil secret names:

- `VLLM_API_KEY`
- `VLLM_INTERNAL_API_KEY`
- `FINITE_USAGE_API_SERVICE_KEY`

Never commit secret values. Every container release must pin image digests,
model revision, and modelwrap metadata, then publish measured
`tinfoil-deployment.json` and `tinfoil.hash` assets before deployment.

