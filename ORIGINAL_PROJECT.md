# Original ApprovalMatch architecture and research

> **Important:** The root website in this repository is a simplified, standalone reconstruction. It is **not yet the complete original application**. The original source package must be imported before claiming the full OCR workflow, research code, and test suite are present here.

## Original app and demonstration

- Original public demonstration: https://carebridge-aarush.simplyaarush.chatgpt.site/
- Goal: help patients check whether hospital financial assistance they have already been approved for is reflected in their bill, and prepare questions for the billing office.
- Primary inputs: approval letter, latest hospital bill, payment records, or manually typed fields.
- Output: clear account comparison, clarification flags, suggested next steps, and a printable/shareable report.
- Optional local case saving and follow-up tracker were part of the original workflow.

## Model and processing pipeline

1. **Photo recognition** — Tesseract.js 6.0.1 with a **pretrained English LSTM OCR model** reads images. The model was not trained from scratch by this project.
2. **Extraction** — JavaScript extracts candidate provider, account, service dates, statement dates, coverage, amounts, and payment details from recognized text.
3. **Human confirmation** — users inspect and correct extracted fields. Manually typed details skip OCR.
4. **Matching and validation** — deterministic checks identify conflicting accounts, providers, dates, coverage, invalid amounts, duplicate records, and missing evidence. Conflicting records pause the comparison rather than being silently merged.
5. **Financial explanation** — integer-cent calculations compare the original patient responsibility, approved relief, payments, and current balance; potential balance correction and potential refund are reported separately.
6. **Patient report** — browser-generated explanations and billing-office follow-up material.

Conceptual flow:

```text
Approval letter + bill + payment records
                  |
       Photo OCR or typed entry
                  |
        Extract candidate fields
                  |
        User review and correction
                  |
       Check accounts/dates/coverage
            /               \
    Needs clarification    Valid match
            |                  |
       Explain gaps      Compare balances
                               |
                   Report and follow-up
```

## Original module names

- `ocr-engine.js` — browser OCR
- `extraction.js` — candidate field extraction and account consistency
- `match-engine.js` — validation and matching rules
- `money-explanation.js` — money calculations and patient explanation
- `match-view.js` — match presentation and printable report

These module names describe the original implementation; they are **not included in this simplified repository yet**.

## Verification and limits

The earlier development record described **35 automated tests**, including **500 varied synthetic ledger calculations** checked against an independent calculation. The research package also contained synthetic OCR evaluations. These results refer to the earlier source package and **cannot be reproduced from this repository until that package is imported**. Synthetic evaluations do not establish accuracy on real patient documents, confirmed refunds, savings, or independent clinical/financial review.

An experimental classifier was researched but **disabled in the user-facing decision flow**. There is no basis to describe ApprovalMatch as a custom-trained financial eligibility AI, a medical coding validator, or an automated refund service.

## Example demonstration case

A fictional walkthrough used account `DEMO-110`, 80% assistance approval, $1,000 original responsibility, $300 already paid, and a $700 current balance. It illustrates the distinction between a potential balance correction and potential refund; a provider must verify any real outcome.

## Privacy, safety, and authorship

- The original browser workflow processed data locally; do not upload real patient information or unredacted records to GitHub.
- No live hospital ledger or insurer integration, money transfer, or automatic eligibility determination is implied.
- Substantial ChatGPT/Codex implementation assistance was used and should be disclosed accurately.
- The original full source, assets, test suite, and research evaluation files need to be imported from the separately created `ApprovalMatch_CAC_Package.zip` before claiming a complete source release.

## Next source migration

Import the original package's `source/dist`, tests, research scripts, assets, dependency lockfile, and source manifest. Run the packaged test suite and inspect the deployed output. Replace the simplified root interface with the verified original build, then configure GitHub Pages for the correct build directory. Do not publish credentials, private data, or third-party assets without appropriate rights.
