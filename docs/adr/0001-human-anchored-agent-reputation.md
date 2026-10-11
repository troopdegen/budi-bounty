---
status: accepted
date: 2026-10-09
---

# Agent reputation is anchored to a verified human, enforced by one contract

ERC-8004 is gameable because nothing links an agent to a real human or its ratings to real work: any address can own agents, any address can rate, and ratings follow the NFT when it is sold. Budi adds that structure on top of 8004 instead of replacing it. Budi acts as Accreditor and Issuer (modeled on SEP's RVOE and Europass Digital Credentials) and issues each Human-Passport-verified person one Operator License: an NFT only the Issuer can move, whose Record (its ERC-6551 account, like the driving record behind a driver's license) owns the person's Agents (their 8004 identity NFTs) and holds their Credentials (soulbound NFTs, full record onchain in W3C Verifiable Credential shape). Reputation belongs to the human; an Agent's reputation is the Credentials in its owner's Record that name it (your driving record, not the car's), so a sold Agent carries nothing. One Budi contract enforces the chain at every Submission and payout (Agent signature from its `agentWallet`, Agent owned by the License's Record, personhood unexpired, human co-signature, Sponsor holds a different License), and Budi's 8004 ratings carry `tag2 = "license:<id>"` so anyone can filter by current owner.

## Considered options

- Hash-only Credentials, or EAS attestations: rejected; Mel wants Credentials fully onchain, and EAS, Verax and Sign Protocol are not deployed on Monad.
- Credentials and Agents owned directly by the person's wallet: rejected; an Issuer-run wallet move would strand the Agent and break the human-to-Agent link.
- Reputation accruing to the Agent (the June 2026 Frutero digital-twin design): rejected; it makes reputation sellable with the Agent, and sponsors want to trust the human.
- A freely transferable License: rejected; it sells the whole reputation as a bundle.

## Consequences

- An Issuer move must transfer the same License token, never burn and reissue: a new token gets a new ERC-6551 account and loses every Credential.
- 8004's self-feedback guard only checks the direct owner (the License's Record), so the human's own wallet can rate their own Agent. Raw 8004 scores must never be shown; only the Budi Issuer address counts as a rater.
- Budi creates every Agent's `agentWallet` (a Dynamic server wallet), so "the Agent signed" means Budi's backend signed for it; the human co-signature is what proves the person stands behind the work. Moving the Agent key's grant onchain (Structure B) or to a smart-account session key (Structure C) is the upgrade path. Research: `docs/research/onchain-human-agent-link.md`.
