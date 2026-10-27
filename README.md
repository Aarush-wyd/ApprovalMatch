# ApprovalMatch
### Follow Your Approved Hospital Relief

**A browser-based tool to help patients check whether approved hospital financial assistance is reflected in their bills.**

[**Try the original live app**](https://carebridge-aarush.simplyaarush.chatgpt.site/) · [**Watch my Congressional App Challenge demonstration**](https://www.youtube.com/watch?v=C_lFDgLhY8s) · [**Read my project story**](PROJECT_STORY.md)

> **Source release status:** This public repository documents my original project, but **does not yet contain the complete original application archive**. The files currently at the repository root are a **smaller demonstration**, not the full OCR-enabled app. The complete original source was packaged separately as `ApprovalMatch-Source-Code(1).zip` (104 archive entries, approximately 47.5 MB uncompressed, including large OCR binaries). I was unable to transfer that complete package through the GitHub integration used to prepare this repository. This is a transfer limitation, **not a claim that GitHub prohibits these files**. The original app is accessible through the live link above; the complete ZIP has not been uploaded or attached to this repository. I am documenting the contents and setup below so the public can understand exactly what was built and what remains to be published.

## Why I created ApprovalMatch

I wanted to help people who have already qualified for hospital financial assistance but still struggle to understand whether that assistance has actually been applied. Comparing approval letters, bills, insurance statements, and receipts can be overwhelming, particularly for patients and families unfamiliar with medical or financial terminology. My goal was to organize that information and give patients a clearer starting point for contacting the billing office.

## What the original app does

The original version guides a patient through three stages:

1. **Gather and review information.** Enter approval details, hospital charges, and payments manually or use a photo or document. Local OCR suggests text and fields; the user confirms them.
2. **Check whether records belong together.** Compare hospitals, account identifiers, service dates, and approval coverage. Incomplete or conflicting records trigger a hold or request for review rather than a definitive financial conclusion.
3. **Explain and follow up.** Compare approved assistance against billed and paid amounts, distinguish a possible balance correction from a possible refund, and prepare a printable report with questions for the hospital billing office.

The original app includes browser-based photo input, document-type guidance, extraction review, local PDF processing, report preparation, follow-up organization, and an optional local case-saving feature. It runs in desktop and mobile browsers, including Android Chrome. **It is not an Android APK or Play Store application.**

## Technology and architecture

| Component | Original implementation |
| --- | --- |
| Front end | HTML, CSS, JavaScript, responsive browser UI |
| OCR / machine learning | Tesseract.js 6.0.1 with pretrained English LSTM weights, processed locally in the browser |
| PDF handling | PDF.js and pdf-lib assets, with their original third-party notices |
| Field extraction | Parsing of account numbers, dates, assistance amounts, and payment information; manual review required |
| Record matching | Rule-based checks for hospital, account, service dates, coverage, and conflicts |
| Financial logic | Integer-cent calculations and separate balance-correction / possible-refund explanations |
| Reports | Browser-generated printable summaries and supporting PDF preparation |
| Research | Synthetic OCR benchmarks, classifier experiments, manifests, results, and scripts |
| Validation | Node.js test suite and independent BigInt-based checks of synthetic ledger calculations |

**AI is used for text recognition, not for making final billing decisions.** The OCR model is pretrained; I did not train a custom OCR model. An experimental document classifier was also evaluated on small, fictional datasets. Its later challenge performance was limited, so automatic document-type suggestions were disabled in the final interface. Financial comparisons remain rule-based.

## What is inside the complete source archive?

The separate `ApprovalMatch-Source-Code(1).zip` contains **104 entries** (including directories where present), approximately **47.5 MB uncompressed**. Important files include:

```text
ApprovalMatch/
├── README.md
├── AI_USE.md
├── LICENSE
├── package.json
├── package-lock.json
├── .github/workflows/pages.yml
├── dist/
│   ├── index.html
│   ├── app.js
│   ├── style.css
│   ├── studio.css
│   ├── guided-view.js
│   ├── match-view.js
│   ├── match-engine.js
│   ├── money-explanation.js
│   ├── ocr-engine.js
│   ├── extraction.js
│   ├── photo-input.js
│   ├── document-model.js
│   ├── pdf-export.js
│   ├── engine.js
│   ├── hospitals.js
│   ├── studio.js
│   ├── credits.html
│   ├── source-code.html
│   └── assets/
│       ├── ocr/                 # traineddata, WebAssembly engines, workers, licenses
│       ├── model-card.json
│       ├── pdf-lib.min.js
│       ├── pdf.min.mjs
│       ├── pdf.worker.min.mjs
│       ├── icon.svg
│       └── third-party notices and supporting PDF
├── tests/
│   ├── core.test.mjs
│   ├── extraction.test.mjs
│   ├── match.test.mjs
│   ├── money-explanation.test.mjs
│   └── studio.test.mjs
└── research/
    ├── TESTING.md
    ├── generate-ocr-fixtures.py
    ├── generate-ocr-challenge.py
    ├── test-models.mjs
    ├── test-ocr-challenge.mjs
    ├── model-test-results.json
    ├── ocr-challenge-results.json
    ├── ocr-fixtures/           # synthetic images and labels
    └── ocr-challenge/          # additional synthetic images and labels
```

The bundled English OCR traineddata alone is about **10.9 MB**, and the archive also includes multiple multi-megabyte WebAssembly engines and JavaScript loaders. These binaries are a significant part of the package size.

## Development and testing

My original development record describes **35 automated tests**, including **500 varied synthetic ledger calculations** compared with a separate BigInt reference implementation. These are code-level checks, not evidence that the app accurately handles every hospital bill.

The research archive also records:

- An initial **16-image synthetic OCR set** from four fictional document layouts under clean and degraded conditions: **53/56 exact fields** and approximately **0.22% aggregate character error** in that controlled set.
- A separate **24-image synthetic OCR challenge** across eight fictional layouts and three variants: **46/51 expected fields correct**, **20/24 documents entirely exact**, with account-number recognition errors and omitted fields.
- An experimental document classifier that scored **16/16** on a tiny synthetic development holdout but **7/12** on a later challenge, compared with **6/12** for a keyword baseline. The classifier was **not enabled** for automatic patient-facing document classification.

These evaluations used **fictional documents**, not real patient records or independent clinical validation. The original archive contains the underlying scripts, manifests, and results. The test suite has **not been fully reverified from this GitHub checkout**, because the original tests and dependencies have not yet been imported.

## How to run the complete original package locally

These instructions apply to the **separate original ZIP**, once obtained and extracted—not to the smaller GitHub-root demonstration.

1. Extract the ZIP and open its inner `ApprovalMatch` directory.
2. Install Node.js 20+ to run tests.
3. From that directory run:

```bash
npm ci
npm test
python3 -m http.server 8000 --directory dist
```

Open `http://localhost:8000`. The web app itself is static and does not require an npm build. Camera access requires browser permission and HTTPS or localhost. The original package also includes `research/TESTING.md` for reproducing synthetic OCR evaluations.

## Why the complete code is not on GitHub yet

I prepared the source as a ZIP with the original application, OCR weights, PDF assets, tests, and research. The available GitHub editing integration successfully published text documentation and a smaller demonstration, but **could not complete the bulk transfer of the original archive and its large binary assets**. I have therefore kept this README explicit rather than implying that the complete source has already been released.

The archive can be uploaded later using a normal local Git client or a suitable bulk-upload method. Once imported, the original `dist/` folder can be deployed with the repository's GitHub Pages workflow. **GitHub Pages deployment of the original app has not been verified.** The original live demo link above is a separate hosting location.

For step-by-step import instructions, see [IMPORT_ORIGINAL_SOURCE.md](IMPORT_ORIGINAL_SOURCE.md). For additional technical background, see [ORIGINAL_PROJECT.md](ORIGINAL_PROJECT.md).

## Privacy, accuracy, and limitations

- OCR and document processing occur locally in the browser after assets are loaded; there is no patient-document upload endpoint in the documented original app.
- Users must confirm extracted fields. OCR can misread names, dates, account IDs, and amounts.
- Optional browser case storage is not encrypted. Avoid entering real patient information on shared devices.
- The app does not access hospital accounts, approve assistance, submit claims, verify insurance coverage, or guarantee a refund.
- Any possible balance adjustment or refund must be confirmed by the hospital or insurer.
- No real patient records, independently verified patient savings, or recovered refunds are claimed.

## My contributions and AI assistance

I chose the problem and intended users, directed the three-step experience, requested and reviewed design changes, refined the distinction between balance corrections and refunds, and prepared the demonstration. **ChatGPT and Codex provided substantial assistance with implementation**, including generating and revising code, debugging, interface development, automated checks, animations, and deployment materials; Cursor was also used for interface support. I did not train the Tesseract OCR model.

This disclosure matters because using AI assistance is different from claiming to have written all the code independently. The original package contains a more detailed `AI_USE.md` record.

## More information

- [My project story and Congressional App Challenge responses](PROJECT_STORY.md)
- [Technical architecture and development notes](ORIGINAL_PROJECT.md)
- [Original-source import instructions](IMPORT_ORIGINAL_SOURCE.md)
- [Demonstration video](https://www.youtube.com/watch?v=C_lFDgLhY8s)
- [Original live application](https://carebridge-aarush.simplyaarush.chatgpt.site/)

## License

The code currently published in this repository is under the [MIT License](LICENSE). The original archive also contains an MIT license for the project code; bundled third-party OCR, PDF, and hospital materials retain their own notices and rights.
