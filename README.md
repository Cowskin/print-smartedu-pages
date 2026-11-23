# Print SmartEdu pages

A reusable skill for printing or exporting specific pages from [国家中小学智慧教育平台](https://basic.smartedu.cn) (`smartedu.cn` / `ppt.basic.smartedu.cn`).

## Use this when

The user sends a SmartEdu viewer link and asks to print, export, or save a page range (for example pages 151–153).

## Install

Copy `SKILL.md` into your assistant's skills folder as `print-smartedu-pages/SKILL.md`. In Grok Bot, you can also add it from your skill library.

## What it does

1. Opens the exact viewer URL (including the `#/view?...` fragment).
2. Signs in when the site requires it, and solves common puzzle captchas.
3. Exports only the requested pages to a print-ready PDF, with viewer chrome cropped out.
4. If asked to print, sends the PDF to the user's default printer (A4, fit-to-page) and waits for the job to finish.

The viewer is often a textbook or courseware document, not a PowerPoint. Viewer page numbers may differ from the printed textbook page numbers; both are reported.

## Security

Do not put SmartEdu usernames or passwords in this skill or in chat replies. Use a password vault or a one-time sign-in form.
