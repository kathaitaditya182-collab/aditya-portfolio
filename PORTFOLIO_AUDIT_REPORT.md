# Portfolio Audit Report

## Completion addendum — 2026-10-30

The original audit below is retained as a record of findings at audit time. Subsequent implementation and validation results are tracked here.

### Fixes implemented

- Rewrote the README for Aditya Kathait's digital marketing portfolio and corrected the email, LinkedIn, GitHub profile, and portfolio links.
- Updated the resume PDF's visible portfolio domain and hyperlink; updated the resume viewer canonical URL. The PDF remains one page and its experience, education, and six certifications were preserved.
- Removed UIMT College from the active project list and campaign gallery. Its image file remains in the repository, unreferenced.
- Removed the missing whoosh sound effect and call; retained the existing background music control.
- Removed placeholder `#` project destinations and display the “Visit” control only for projects with destinations.
- Renamed “View Full Portfolio” to “View Resume.”
- Removed Uttarakhand Travel App from active project cards as requested. Its image asset remains untouched.
- Corrected the original audit tally: there were five placeholder project destinations, not four. After removals, active project data contains no `#` destinations.

### Remaining findings

- Resume achievement metrics and the published phone number remain unverified by the user; no numbers were invented or changed.
- Twenty-two image files are currently unreferenced, including the retained UIMT and Uttarakhand Travel App images. They were not deleted because their ownership/need was not proven.
- No `package.json` or application source tree exists; the repository is a static deployment with a prebuilt React/Three.js bundle. `npm run build` is therefore unavailable. No artificial package manifest was added.
- Live desktop/tablet/mobile browser testing and deployed Vercel verification remain unverified because browser automation and deployment status access were unavailable.
- The `origin` branch was two commits ahead at the start of this execution. Existing commits were preserved.

### Validation results

- **PASS:** JavaScript syntax check (`node --check` on the deployed bundle).
- **PASS:** Static HTML internal-link and referenced-image/model/media checks; no missing local references found after the fixes.
- **PASS:** GLTF buffer/image URI scan; all referenced local model resources exist.
- **PASS:** Resume PDF text/link checks for the supplied identity, portfolio URL, experience, education, and six certifications; old portfolio domain absent from searchable text.
- **PASS:** Resume PDF rendered as one page and visually inspected. Poppler emitted missing local display-font warnings, but the resulting render was legible and retained the original layout.
- **NOT RUN:** Production build; no package manifest or source build process is present.
- **NOT VERIFIED:** Browser console, desktop/mobile responsive behavior, and deployed Vercel revision.
- **PARTIAL:** External link checks. Rishikesh Nomads loaded; the portfolio, GitHub, LinkedIn, and Uttarakhand deployment could not be fetched by the available web reader, so they are not asserted live.
- **PASS:** No tracked `.env.local`; it remains ignored. No secret values were printed or added to Git.

### Git and deployment

The repository-local Git identity is Aditya Kathait <kathaitaditya182@gmail.com>. The original fix commit is `346eb7b9fbddfe175e4426535e6d0a9b41e66836`. The audit report is included in this repository. Push/deployment status will be recorded after the final commit and push attempt.

**Audit date:** 2026-10-30  
**Scope:** Checked-out repository contents, static asset references, bundled React application strings, HTML pages, README, local resume PDF text, and `.env.local` tracking status. The deployed URL could not be opened through the available web reader, and no interactive browser session was available. Live desktop/tablet/mobile behavior, console output, and deployed response status are therefore **not verified**.

## Summary

| Measure | Count | Notes |
|---|---:|---|
| Reported finding entries | 15 | Includes confirmed defects and clearly labeled manual-review items. |
| Identity-related entries | 4 | Wrong repository identity, contact details, resume portfolio URL, and phone-publication check. |
| Other people's names/handles in portfolio context | 1 | `Sunil56224972` in the README GitHub URL. Third-party dependency and model author credits are excluded. |
| Incorrect or placeholder link instances | 10 | Two README GitHub URLs (badge and clone command), one LinkedIn `#`, one wrong email link, five project `#` links, and one resume portfolio URL. The misnamed “View Full Portfolio” control is described separately because its URL does open a page. |
| Broken image assets | 0 | All image paths referenced by the checked-in HTML and bundle resolve locally. |
| Broken media assets | 1 | A music file referenced by the bundle is absent. |
| Technical findings | 8 | Includes broken/no-op navigation, missing media, build/source maintainability, SEO, accessibility, and responsive risks. Categories overlap. |
| Confirmed security issues | 0 | No credential value was printed or found in tracked source. `.env.local` is ignored and untracked; it contains a `VERCEL_OIDC_TOKEN` variable locally. |

Severity labels follow the requested scale. “Needs manual review” means the repository alone does not establish that the content is false or unauthorized.

## Findings

### 1. README links to another GitHub account and repository

- **Severity:** HIGH
- **Location:** `README.md:2`, `README.md:58`
- **What is wrong:** The README badge and clone command point to `github.com/Sunil56224972/aditya-kathait`, while the supplied owner account is `kathaitaditya182-collab`. The account handle introduces another person's identity into the repository documentation.
- **Why it matters:** A recruiter following the repository link may land on another owner's account or an unrelated repository, undermining confidence about who owns the portfolio.
- **Recommended fix:** Replace both repository URLs with the verified repository under the supplied GitHub account, or remove the README badge and clone instructions if the repository is not public under that account.

### 2. README contact links contain a placeholder and a mismatched email

- **Severity:** HIGH
- **Location:** `README.md:77-78`
- **What is wrong:** LinkedIn points to `#`, and the email link uses `adityakathait182@gmail.com`, which does not match the supplied correct email `kathaitaditya182@gmail.com` or the email in the resume and application bundle.
- **Why it matters:** The LinkedIn link does not reach a profile, and prospective contacts may send messages to the wrong address.
- **Recommended fix:** Use the verified LinkedIn URL and correct the email link and visible address to the supplied identity details.

### 3. Resume PDF contains a different portfolio domain

- **Severity:** HIGH
- **Location:** `Aditya_Kathait_Resume_ATS.pdf`, page 1 (embedded contact details)
- **What is wrong:** The resume prints `adityaportfolioo-one.vercel.app`, while the supplied live portfolio is `aditya-portfolio-phi-fawn.vercel.app`.
- **Why it matters:** Recruiters using the resume may reach an outdated or unrelated site. This is a confirmed identity/contact inconsistency between the PDF and the supplied canonical URL.
- **Recommended fix:** Update the resume source with the verified portfolio URL and re-export it. The PDF text extraction also shows replacement characters in several bullets/date separators; inspect the rendered PDF and correct the source encoding if those glyphs appear in the actual document.

### 4. Resume exposes a phone number; public-sharing intent needs confirmation

- **Severity:** MEDIUM — NEEDS MANUAL REVIEW
- **Location:** `Aditya_Kathait_Resume_ATS.pdf`, page 1
- **What is wrong:** The public-facing resume contains a mobile phone number. No expected number was supplied for comparison, so correctness cannot be verified from this audit brief.
- **Why it matters:** The number may be intentional contact information, but publishing it also makes it available to scraping and unsolicited contact.
- **Recommended fix:** Confirm that the number is current and that you want it publicly displayed. If not, remove it from the resume and its public download.

### 5. Resume achievement figures are not independently substantiated by the supplied facts

- **Severity:** MEDIUM — NEEDS MANUAL REVIEW
- **Location:** `Aditya_Kathait_Resume_ATS.pdf`, page 1
- **What is wrong:** The resume includes claims such as 170+ listings, audience engagement moving from 10–15% to 35–40%, 2,000–2,500 monthly organic reach, and a 120+ member WhatsApp community. The supplied expected resume facts do not confirm or contradict these figures.
- **Why it matters:** Quantified results are persuasive but should be supportable in an interview and consistent with source records.
- **Recommended fix:** Verify each figure, its measurement period, and the meaning of the metric against records before retaining it. No figures were changed or presumed false in this audit.

### 6. UIMT College is presented as a portfolio project and campaign image

- **Severity:** MEDIUM — NEEDS MANUAL REVIEW
- **Location:** `creative-campaigns.html:86`; bundled project data in `assets/index-D_hQMIQo.js` (single minified line)
- **What is wrong:** UIMT College appears as a project titled “Digital marketing for admissions” and as a campaign image. The image is a screenshot of the UIMT website with a person's portrait visible. UIMT is not in the supplied education history, which names D.D. College. The asset may represent legitimate client work; the repository alone cannot establish the relationship or image-use rights.
- **Why it matters:** Without context, a viewer could mistake UIMT for Aditya's college or assume the screenshot/portrait is original work or an authorized case study.
- **Recommended fix:** If this is client work, label the relationship and project contribution clearly and confirm permission to display the screenshot. If it is unrelated or unauthorized, remove it from the portfolio after review. Do not change the education section to UIMT based on this asset.

### 7. README describes a developer portfolio with unrelated project claims

- **Severity:** MEDIUM
- **Location:** `README.md:28-50`, `README.md:75`
- **What is wrong:** The README positions the site as a React/Three.js developer portfolio and lists projects such as Bilaspur College Reviewer, GreenBow, Retro Green ASCII Bio, Dither Core, and Fav Panda Portfolio. The current site bundle presents a digital marketing portfolio. The README also says “Aditya Kathait serves as the central hub” and closes with an incomplete-sounding “part of your visions.” These may be old project references, but their ownership and relevance are not established by the supplied facts.
- **Why it matters:** The README conflicts with the live portfolio's professional positioning and can make both the work history and project ownership unclear.
- **Recommended fix:** Rewrite the README to describe the current portfolio accurately. Retain only projects Aditya can substantiate and identify the role/contribution for each; correct the awkward contact sentence.

### 8. Five project cards use `#` instead of working destinations

- **Severity:** MEDIUM
- **Location:** `assets/index-D_hQMIQo.js`, bundled project data (`NC`, single minified line)
- **What is wrong:** The “Freelance Poster & Carousel Samples,” “Social Media Marketing,” “AI-Generated Posters,” “Marketing Creatives,” and “Instagram Campaigns” cards each have `link:"#"`. These controls do not navigate to a case study, campaign, or external destination.
- **Why it matters:** The cards look interactive but do not let visitors inspect the work or verify the claims.
- **Recommended fix:** Link each card to an appropriate case study or gallery item, or render it as non-clickable content until a destination exists.

### 9. “View Full Portfolio” opens the resume page

- **Severity:** MEDIUM
- **Location:** `assets/index-D_hQMIQo.js`, navigation component `tne` (single minified line)
- **What is wrong:** The “View Full Portfolio” anchor targets `/./resume.html`. The destination is a resume viewer, not a full-portfolio page.
- **Why it matters:** The label sets the wrong expectation and duplicates the separate resume action.
- **Recommended fix:** Point it to the intended portfolio destination or rename it to “View Resume.”

### 10. Background music references a missing audio file

- **Severity:** MEDIUM
- **Location:** `assets/index-D_hQMIQo.js`, audio component; expected `/music/simple-whoosh-03-433005.mp3`
- **What is wrong:** The bundle references `/music/simple-whoosh-03-433005.mp3`, but the only checked-in music file is `music/background.mp3`.
- **Why it matters:** Any interaction that requests the missing sound can fail and may log a browser media/network error.
- **Recommended fix:** Add the intended licensed audio asset or change the reference to an existing file. If the sound is not needed, remove its reference.

### 11. Twenty-one image files are not referenced by the current pages or bundle

- **Severity:** LOW — NEEDS MANUAL REVIEW
- **Location:** `images/` (21 unreferenced files; see examples below)
- **What is wrong:** Static reference scanning found 21 image files not used by `index.html`, `resume.html`, `creative-campaigns.html`, the bundled JS/CSS, or `src/style.css`. The set includes screenshots named for older developer projects (`Bilaspur_CollegeReviewer--Ai-Integrated_website.png`, `GreenBow---The-Intro.png`, `dither_core.png`, `fav-panda-portfolio.png`) and other files such as `amaya.webp` and `zennah.webp`.
- **Why it matters:** These may be stale project assets or legitimate source material. Their provenance and ownership cannot be determined from filenames, and their presence increases repository size and makes asset ownership harder to audit.
- **Recommended fix:** Inventory the files and confirm ownership/relevance. Remove or archive them only after review; do not replace or delete images as part of this audit.

### 12. Main page lacks search and social preview metadata

- **Severity:** MEDIUM
- **Location:** `index.html:3-9`
- **What is wrong:** The main page has a title but no meta description, canonical URL, Open Graph tags, or Twitter card metadata. No `robots.txt` or sitemap is present in the repository inventory.
- **Why it matters:** Search engines and social platforms have little explicit guidance for describing or canonicalizing the portfolio. The lack of a sitemap is a smaller discoverability concern for this very small site.
- **Recommended fix:** Add a concise, accurate description, canonical URL for the chosen production domain, and social preview metadata. Add a sitemap/robots file if search indexing is intended and verify the deployed canonical domain first.

### 13. Campaign gallery alt text is generic rather than descriptive

- **Severity:** MEDIUM
- **Location:** `creative-campaigns.html:74-104`
- **What is wrong:** Most gallery images use labels like “Campaign 1,” “Campaign 2,” and “Campaign 7” rather than describing the image or campaign. The project bundle also uses image-based cards; their accessibility depends on surrounding labels and should be checked in a browser.
- **Why it matters:** Screen-reader users receive little useful information about the work, and image search context is weak.
- **Recommended fix:** Write concise, truthful alt text describing each image's content or role. Use empty alt text only for genuinely decorative images.

### 14. Repository contains a production bundle but no rebuildable app source or package manifest

- **Severity:** MEDIUM
- **Location:** Repository root; `assets/index-D_hQMIQo.js`; `package-lock.json`
- **What is wrong:** The repository has a 1.73 MB minified JavaScript bundle and a 93-byte lockfile, but no `package.json` and no readable React/Three.js application source tree. `src/style.css` exists, but the app implementation is only available as the bundled artifact.
- **Why it matters:** The site may deploy as a static build, but contributors cannot reliably install dependencies, reproduce the build, run defined checks, or maintain the application from this checkout. Dependency versions and vulnerability status cannot be meaningfully audited from the empty lockfile.
- **Recommended fix:** Restore the source project and its package manifest/lockfile, or document that this repository intentionally stores only a generated static export and retain the reproducible source/build workflow elsewhere.

### 15. Resume viewer has a mobile scrolling risk

- **Severity:** MEDIUM — NEEDS LIVE DEVICE/BROWSER REVIEW
- **Location:** `resume.html:11-14`, `resume.html:29-31`, `resume.html:48-54`
- **What is wrong:** The page sets `body { overflow: hidden; }` and relies on a full-height PDF iframe under a fixed 80 px navigation bar. This can make the PDF difficult to scroll or the navigation controls cramped on narrow screens. No tablet/mobile browser rendering was available to confirm the actual result.
- **Why it matters:** Applicants may be unable to read or download the resume comfortably on a phone.
- **Recommended fix:** Check at common phone and tablet widths, including the browser's built-in PDF viewer. Ensure the document remains scrollable and the download/back controls fit without clipping.

## Resume consistency check

- **Name:** Matches the supplied name, Aditya Kathait.
- **Experience:** Digital Marketer at Rishikesh Nomads, February 2024–July 2026; matches the supplied employer, title, and dates. The PDF includes `rishikeshnomads.com`.
- **Education:** BBA Marketing at D.D. College, 2023–2026; matches the supplied institution and dates. Dehradun is also printed as the campus/location.
- **Certifications:** All six supplied certifications are present: Adobe Experience Manager Foundations, Adobe Target Foundations, Adobe GenStudio for Performance Marketing Foundations, Adobe Content Analytics Foundations, Advanced Search Engine Optimization (Semrush), and Social Media Marketing (HubSpot). No additional certificate title was identified in the extracted PDF text.
- **UIMT:** Appears as a marketing project/image, not as the education entry in the resume. Confirm the client-work context manually (Finding 6).
- **PDF freshness:** The only resume PDF found is `Aditya_Kathait_Resume_ATS.pdf`. No second/old resume PDF was identified in the repository inventory.
- **Unverified claims:** Resume metrics and the phone number need owner confirmation (Findings 4–5). No factual content was rewritten.

## Image and asset check

- All image paths referenced by the current HTML and JS bundle resolve to files in the repository; **0 broken image paths** were found.
- One missing media reference was found: `/music/simple-whoosh-03-433005.mp3` (Finding 10).
- Twenty-one image files are not referenced (Finding 11). Unused does not mean unauthorized or incorrect.
- The used `main2.webp` hero image depicts a stylized Japanese torii gate in an illustrated waterscape. This appears to be an intentional visual theme, not a person's portrait. No confirmed template stock headshot or other person's profile avatar was identified in the current page references. UIMT's page screenshot visibly contains a third-party portrait, so verify authorization/context before presenting that image as campaign work.
- No image was changed or replaced.

## Technical, accessibility, and security limits

- The checked-in HTML points to existing bundle and stylesheet paths. A live browser/console run was unavailable, so runtime exceptions, WebGL behavior, interaction completion, and actual desktop/tablet/mobile layouts remain unverified.
- The local `.env.local` file is ignored by `.gitignore` and is not tracked by Git. It contains a `VERCEL_OIDC_TOKEN` variable; its value was not displayed. This is not evidence of a committed or publicly exposed secret. Keep it local and rotate it only if there is evidence it was shared.
- `.vercel/project.json` contains Vercel project/team identifiers, not an API secret. It is local deployment metadata and should remain excluded from public source unless intentionally shared.
- The HTML subpages load Tailwind from `cdn.tailwindcss.com` and Outfit from Google Fonts. They depend on third-party network availability and disclose ordinary request metadata to those providers. No form submission endpoint or analytics/tracking script was found in the inspected page source.
- Vulnerability status cannot be established because the source dependency manifest is missing (Finding 14). No dependency installation or package audit was run.

## Prioritized remediation plan

1. **Fix identity and personal-information mistakes:** correct the README repository/account link, replace the placeholder LinkedIn and mismatched email, correct the portfolio URL embedded in the resume, and confirm whether the resume phone should be public.
2. **Fix resume and content inconsistencies:** rewrite the stale developer-focused README, verify the resume metrics, and clarify whether UIMT is authorized client work rather than education or unrelated content.
3. **Fix broken links and assets:** replace the four `#` project links, correct or rename the “View Full Portfolio” action, and restore or remove the missing audio reference. Review the 21 unused images for provenance before any cleanup.
4. **Fix technical and security issues:** restore the maintainable source/build manifest, then run dependency checks and browser console checks from that source. No committed secret was found in this audit; keep `.env.local` ignored.
5. **Improve design, SEO, and performance:** add metadata after confirming the production canonical domain, improve campaign-image alt text, and test resume readability and interactive layout at desktop, tablet, and mobile sizes. Then assess the large JavaScript bundle and 3D loading on real devices.
