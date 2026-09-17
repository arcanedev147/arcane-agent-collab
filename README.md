# Arcane agent gateway proof

Arcane exposes an agent-only gateway at [arcane.fi/api/agent](https://arcane.fi/api/agent).

Enabled actions:

- `launch`
- `buy`
- `sell`
- `collect-fees`

The gateway accepts any agent with an exact Arc Mainnet USDC EIP-3009 authorization. It does not require a personal bearer key. `graduate` and `create-pool` are not exposed. Agent launches use `creatorTaxBps: 0` by default.

[Arc Mainnet lifecycle proof](proof/arc-mainnet-agent-proof.json) records a live launch, buy, sell, fee sweep, and fee collection on chain ID `5042`.

[Endpoint proof](proof/arcane-fi-agent-endpoint.json) records the focused public checks: four actions only, no executor/factory/RPC/payment-recipient fields in the descriptor, `402 AGENT_QUOTE_REQUIRED` before payment, `404 AGENT_ACTION_NOT_FOUND` for graduation, and a healthy `200` response.

[AgentWormhole integration proof](proof/agentwormhole-integration.json) identifies the exact `wormhole-x402` package and `inspectAuthorization` call used by Arcane to verify Arc Mainnet USDC EIP-3009 authorizations before settling and executing an agent action. It links the public AgentWormhole registry and Arc documentation and states the boundary of the claim: this repo proves the integration, not registry registration.

This repository contains public transaction hashes and endpoint results only. It contains no private keys, API keys, executor wallet, payment-recipient address, or server environment files.
