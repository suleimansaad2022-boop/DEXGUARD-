# GUARDYXIS Security Intelligence Add-on

This is an **add-on**, not a replacement for your current GUARDYXIS design.

## 1. Advanced holder intelligence
Uses RugCheck's Solana token report for top holders, owner addresses, supply percentages, creator data and insider-network information. It calculates top-1/top-5/top-10/top-20 concentration and exposes the raw top-holder table.

## 2. Verified security API layers
- RugCheck Solana token report
- GoPlus Solana Token Security API (second layer when configured)

RugCheck: `GET https://api.rugcheck.xyz/v1/tokens/{mint}/report`
GoPlus: `GET https://api.gopluslabs.io/api/v1/solana/token_security?contract_addresses={mint}`

## Setup
1. Copy `.env.example` to `.env`.
2. Add provider credentials if required.
3. `npm install`
4. `npm start`
5. Backend endpoint: `/api/intelligence/<SOLANA_MINT>`

## Frontend
Add:
`<link rel="stylesheet" href="/guardyxis-security.css">`
`<script src="/guardyxis-security.js"></script>`

Create a result container:
`<div id="security-panel"></div>`

After the existing scanner obtains a mint:
`const data = await GUARDYXIS_SECURITY.scan(mint);`
`GUARDYXIS_SECURITY.render(data, document.querySelector("#security-panel"));`

Provider secrets stay on the server. Never put API keys, private keys or seed phrases in frontend code.

Security scores are automated signals, not proof that a token is safe or unsafe. Missing data remains Unknown.
