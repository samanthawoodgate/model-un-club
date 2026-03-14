Update an existing week's resources for Model UN Club.

Arguments format: `week number - what to change`
Example: `2 - replace the YouTube videos and add a 9th country to the briefs`

$ARGUMENTS

Steps:
1. Check what currently exists in `resources/weekN/` and the corresponding week card in `index.html`
2. Make the requested changes — regenerate files if needed using the same packages (pdfkit, pptxgenjs, docx)
3. Keep the same file naming conventions and branding style
4. Update `index.html` if links or content changed
5. Git commit and push
6. Confirm what was changed
