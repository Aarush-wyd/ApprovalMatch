# Import the complete original ApprovalMatch app

The full original source is in **ApprovalMatch-Source-Code(1).zip**, provided separately. The current GitHub root site is an earlier simplified reconstruction; the original archive has not yet been committed.

## Upload with GitHub's website

1. On your computer, unzip `ApprovalMatch-Source-Code(1).zip`.
2. Open the extracted `ApprovalMatch` folder. You should see `dist`, `tests`, `research`, `.github`, `README.md`, `AI_USE.md`, `package.json`, and `package-lock.json`.
3. On the repository's **Code** tab choose **Add file → Upload files**.
4. Upload the *contents* of the extracted `ApprovalMatch` folder, not the outer folder itself. Retain subfolder paths. For large uploads, use Git locally instead of browser uploads.
5. When GitHub warns about existing `README.md`, `.gitignore`, or workflow files, replace those with the original files from the archive; do not overwrite `dist` with the simplified root files.
6. Commit the changes to `main`. Confirm that `dist/index.html` and `dist/assets/ocr/eng.traineddata.gz` are present.
7. Go to **Settings → Pages → Build and deployment** and select **GitHub Actions** (not Deploy from a branch). The workflow at `.github/workflows/pages.yml` deploys `dist`.
8. Check the **Actions** tab for a successful Pages deployment. Then open https://aarush-wyd.github.io/ApprovalMatch/ .

## Recommended local Git upload (more reliable for large model files)

```sh
git clone https://github.com/Aarush-wyd/ApprovalMatch.git
cd ApprovalMatch
# Copy the CONTENTS of the extracted ApprovalMatch folder into this repository.
git add .
git commit -m "Import original ApprovalMatch source, OCR assets, tests and research"
git push origin main
```

The original OCR weights are about 11 MB, and the complete archive is about 26 MB. Do not upload the ZIP itself as a replacement for extracted source files.

## Verify

```sh
npm ci
npm test
python3 -m http.server 8000 --directory dist
```

Open http://localhost:8000 and try a synthetic example. A missing `pdf-lib` module means `npm ci` has not successfully completed; it is not evidence of a failing financial algorithm.

## Safety and provenance

The model is pretrained OCR; the financial comparisons are rule-based. Use synthetic or redacted data. Keep `AI_USE.md`, original third-party license notices, and research limitations in the public repository.
