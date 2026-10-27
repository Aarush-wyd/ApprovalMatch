# ApprovalMatch

**An open-source, browser-based hospital bill review organizer.**

ApprovalMatch helps patients understand itemized hospital charges, compare billed amounts with insurance payments and adjustments, and generate questions to ask a provider or insurer.

## Features
- Enter itemized bill descriptions and amounts
- Automatically estimate the patient portion for each item
- View totals for billed charges, insurance payments, adjustments, and estimated patient amount
- Flag repeated descriptions and cases where payments plus adjustments exceed the billed amount
- Download a readable text summary for later review
- Mobile-friendly interface that runs without an account or server

## Try it
After enabling GitHub Pages with **Settings → Pages → Deploy from a branch → main → /(root)**, visit:

https://aarush-wyd.github.io/ApprovalMatch/

The Pages link will not work until deployment is enabled.

## Run locally
Clone this repository and open `index.html` in a browser, or run a local static server:

```sh
python3 -m http.server 8000
```

Then visit http://localhost:8000.

## How calculations work
For each line: `estimated patient portion = max(0, billed - insurance paid - adjustments)`. These estimates do not account for all billing rules, deductibles, co-insurance, insurer-specific benefits, or claim processing. Repeated descriptions are only review prompts, not proof of duplicate charges.

## Privacy and limitations
This is a client-side educational demo. The app does not transmit bill data to a server, and it does not store submissions in the repository. Avoid entering patient names, account numbers, or other sensitive health information on shared devices. It cannot automatically validate medical coding, contracted rates, or insurance approval. Confirm all findings with the provider and insurer before deciding what to pay.

## Project history
Created as an accessible patient-support technology concept associated with the 2026 Congressional App Challenge. This repository provides a standalone open-source implementation; it should not be represented as an exact export of any separately hosted original application.

## License
MIT — see [LICENSE](LICENSE).
