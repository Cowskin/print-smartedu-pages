---
name: Print SmartEdu pages
description: Use when the user asks to print, export, or save specific pages from 国家中小学智慧教育平台 (smartedu.cn or ppt.basic.smartedu.cn) textbooks or courseware.
---

# Print or export pages from SmartEdu

## When this applies

A link on `ppt.basic.smartedu.cn`, `basic.smartedu.cn`, or another `smartedu.cn` viewer, plus page numbers (for example 151–153), and a request to print, export, or save those pages.

## What the site is

- This is 国家中小学智慧教育平台. The viewer at `ppt.basic.smartedu.cn/#/view?...` is often a textbook or courseware document, not always a PowerPoint.
- Key query params: `ndrContentId`, `catalogType` (for example `tchMaterial`), and `tenantCode` (for example `zxx`).
- Viewer page numbers (for example 151/174) may differ from the printed textbook page numbers at the foot of the page (for example 144). Use the numbers the user gave, and report both.
- Login is often required at `auth.smartedu.cn`. Follow the sign-in and vault skills. Never store or repeat passwords in this skill or in chat. A slide-to-complete puzzle captcha is common; try it yourself before handing off.
- The site may block cloud IPs. If the page fails to load or challenges you, use the box browser with the user's "Route traffic through this computer" setting if it is on, or reuse an already signed-in session.

## Steps

1. Confirm the exact URL and page range. If the user sent only a link, ask for the pages only when they did not specify them.
2. Open that exact URL in the box browser. The hash-router fragment (`#/view?...`) matters; do not drop it.
3. If a sign-in appears, use a saved vault login for smartedu.cn, or credentials the user sent in chat (do not echo them). Complete captchas yourself.
4. Confirm the correct resource opened (title and `ndrContentId`) and go to each requested viewer page.
5. Produce a print-ready PDF of only those pages:
   - One document page per PDF page, portrait unless the source is landscape
   - Full page visible; crop viewer chrome, toolbars, thumbnails, and the playback bar
   - Save under `/workspace/` with a clear name, such as `smartedu-pages-<start>-<end>.pdf`
   - If the site offers a source PPT, PPTX, or PDF download, download it too, but still make a PDF of just the requested pages
6. Check the PDF: the page count matches the request, and each page is complete and readable (no clipped footnotes or running heads).
7. If the user asked to print:
   - On the computer they sent the message from (or the one they named), find a ready printer (`lpstat -p -d`). Use their default printer unless they named one.
   - Copy the PDF onto that computer, then print with fit-to-page and A4 unless they specified otherwise: `lp -d <printer> -o fit-to-page -o media=A4 <file>`
   - Wait until the job completes or the printer returns to idle. Report a failure, not only that a job was submitted.
8. Tell the user what printed or was saved: the book or presentation title, viewer pages and corresponding textbook pages if shown, a short line on what each page contains, the PDF path, and the printer used. Also send the PDF in chat.

## Do not

- Do not put credentials, phone numbers, or passwords in this skill or in replies.
- Do not print or export the entire document when they asked for specific pages.
- Do not assume the viewer is a PowerPoint; treat it as a paged document.
