# ApprovalMatch

**Helping patients understand hospital bills and check whether approved financial assistance has been applied.**

I created ApprovalMatch for the 2026 Congressional App Challenge to address a frustrating problem: receiving financial assistance from a hospital does not always make it easy to understand the bill that follows. ApprovalMatch helps patients organize their documents, compare important amounts, and prepare clear questions for the billing office.

**[Explore the original app demo](https://carebridge-aarush.simplyaarush.chatgpt.site/)** · **[View the project architecture](ORIGINAL_PROJECT.md)**

## Why I built it

Hospital bills can be difficult to understand, especially when a patient has an approval letter, payment records, and multiple statements with different amounts. I wanted to create a tool that brings those details together in one place, highlights inconsistencies, and makes the next step easier.

## How ApprovalMatch works

1. **Add documents or enter details.** The original app accepts hospital bills, financial-assistance approval information, and payment records.
2. **Read and review.** A pretrained OCR model helps turn document images into editable text. Users check the extracted details before proceeding.
3. **Match records.** JavaScript rules check account numbers, providers, dates, coverage, and amounts. Missing or conflicting information is flagged instead of silently combined.
4. **Understand the numbers.** The app distinguishes a possible remaining-balance correction from a possible refund for money already paid.
5. **Prepare a report.** Patients can generate a plain-language summary to discuss with the hospital.

## Technology

| Area | Implementation |
| --- | --- |
| Interface | HTML, CSS, JavaScript |
| Document recognition | Tesseract.js 6.0.1, pretrained English LSTM OCR |
| Data extraction | JavaScript parsing and editable review fields |
| Matching | Rule-based account, provider, date, and coverage checks |
| Financial calculations | JavaScript comparison and explanation logic |
| Reports | Browser-generated printable summaries |

**The machine-learning component is OCR.** I did not train a new OCR model, and the app does not use an AI model to decide whether a patient qualifies for financial assistance. An experimental classifier was explored during development but was not enabled in the patient-facing workflow.

## Testing and research

The original development package documented **35 automated tests**, including **500 synthetic ledger cases** checked against a separate calculation. It also included synthetic OCR evaluation scripts and research materials. These are development tests, **not** evidence of real-world patient accuracy, recovered refunds, or verified savings.

The original test suite and OCR assets are not yet included in this repository. See [Original project architecture](ORIGINAL_PROJECT.md) for the implementation breakdown and limitations.

## Try the code in this repository

The current root website is a **lightweight, standalone bill-review demo**. It is not yet the complete original OCR-enabled app.

To run this version locally:

```bash
git clone https://github.com/Aarush-wyd/ApprovalMatch.git
cd ApprovalMatch
python3 -m http.server 8000
```

Open `http://localhost:8000` in your browser. This version lets you enter charges, review estimates and possible repeated descriptions, and download a text summary.

I am preparing the complete original source for publication. The [source import guide](IMPORT_ORIGINAL_SOURCE.md) explains the repository structure and deployment steps.

## Privacy and limitations

ApprovalMatch is an educational tool for organizing information, not an official billing decision, insurance determination, or refund service. A provider or insurer must verify any adjustment or refund. Do not upload personal medical records, account numbers, or other sensitive information to this public GitHub repository.

## Development and attribution

I developed the project concept, use case, and presentation, with substantial implementation assistance from ChatGPT and Codex. The OCR component uses the pretrained Tesseract engine. The original project materials contain additional development and third-party attribution notes; I intend to preserve those with the full source release.

## License

This repository is published under the [MIT License](LICENSE).
