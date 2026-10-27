# ApprovalMatch — Congressional App Challenge 2026

## Project

**App name:** ApprovalMatch  
**Platform:** Web (phone and desktop browsers)  
**Languages:** JavaScript, HTML, CSS  
**Demo video:** https://www.youtube.com/watch?v=C_lFDgLhY8s  
**Live original demonstration:** https://carebridge-aarush.simplyaarush.chatgpt.site/

## What my app does

ApprovalMatch helps patients who have already been approved for hospital financial assistance check whether their bills reflect that approval.

Users follow three guided steps to enter their approval details, hospital charges, and payments. They can type information or upload a document or photo. Optical character recognition extracts text from images, and users review the information before continuing.

The app checks whether records match by hospital, account, and service dates. It compares approved assistance with billing information and separates a possible balance correction from a possible refund. Conflicting records trigger a review rather than a confident answer.

Finally, ApprovalMatch creates a report patients can share with the hospital billing office. It organizes information, explains calculations, and provides questions to ask. The hospital makes the final decision about any correction or refund.

ApprovalMatch runs in a browser on phones and computers. Document images are processed locally in the browser.

## What inspired me

I wanted to address a healthcare problem that continues after someone receives treatment: understanding and managing the bill.

While researching hospital financial assistance, I learned that receiving approval does not always mean every related bill or payment has been correctly adjusted. Patients may have to compare an approval letter, billing statements, and receipts themselves. That can be confusing, especially when someone is recovering from an illness or helping a family member.

I was particularly interested in the gap between being approved for help and knowing whether that help actually appears in the financial records. ApprovalMatch focuses on that gap.

My goal was to give patients a clear starting point: organize their documents, understand what may need correction, and approach the hospital with a specific question and supporting evidence.

## Technical challenges

One major challenge was handling information from different documents without treating every extracted number as correct. Hospital bills and approval letters use different layouts, and image recognition can confuse dates, account numbers, and amounts. The app asks users to review extracted information before using it.

Another challenge was deciding when records should be compared. Two documents can look related but refer to different accounts, hospitals, or service dates. Checks flag conflicting or incomplete information and pause comparison when necessary.

The financial calculations also needed to distinguish money still owed from money already paid. A balance correction and a possible refund are different outcomes, so the app presents them separately. Calculations use integer cents to avoid rounding problems.

The original development record included 35 automated tests and 500 varied ledger calculations checked against a separate reference calculation. These checks evaluate programmed behavior; they do not establish accuracy across every real hospital document. The full original test suite is not yet present in this GitHub repository.

## What I would improve in version 2.0

For a second version, I would prioritize testing with consenting patients, caregivers, and hospital financial counselors. Their feedback would help improve the questions, document review, and final report.

I would expand support for different hospital document layouts and evaluate text extraction using a larger, permission-based collection of redacted documents. The app could highlight uncertain fields more clearly and help users identify missing information.

Other improvements would include additional languages, stronger accessibility testing, and more hospital-specific assistance resources. An optional follow-up tracker could help patients record calls, requested documents, and the hospital's response.

The goal would remain the same: make billing information easier to understand while keeping patients in control and leaving final financial decisions to the hospital.

## AI and my contributions

I used ChatGPT and Codex for substantial development assistance, including generating and revising code, debugging, building automated checks, improving the interface, and producing presentation and animation materials. I also used Cursor for interface development support.

My direct contributions included choosing the problem, defining the intended users and three-step experience, directing feature and design changes, reviewing examples and explanations, and recording the presentation. I repeatedly revised the project requirements to make the app easier to understand and to separate possible balance corrections from possible refunds.

Within the app, Tesseract.js uses a pretrained text-recognition model to extract text from document images. I did not train that model. Users review extracted information before it is used. Financial comparisons follow programmed rules rather than relying on a language model to decide what someone is owed.

## What I learned

I learned that creating a useful app requires more than getting a calculation to work. The app also needs to recognize when information is incomplete, explain its results clearly, and help someone take a practical next step.

This project helped me understand document recognition, browser-based processing, financial calculations, and automated testing. It also taught me why testing calculations is different from proving that an app works accurately for every real user.

The biggest lesson was the importance of narrowing a problem. ApprovalMatch became more useful when it focused on helping patients compare an existing assistance approval with their billing records.

I also learned to evaluate AI-generated work critically. AI accelerated development, but its output still needed review, corrections, and testing.

## Public release notes

This file documents the original project. The GitHub root site currently contains a smaller demo. The original OCR-enabled source, binary assets, and tests must be imported from the original source archive before the GitHub repository is a complete source release.
