# barcode417-check

Local-only page that shows and decodes the PDF417 barcode on **every page** of a PDF, and checks each one against the page number printed at the bottom (e.g. `2/5`).

**Live:** https://butra.github.io/barcode417-check/

Open `index.html` in a browser (double-click works, no server needed) and drop a PDF anywhere on the page:

- each page gets a card with the barcode image, the decoded text (page field highlighted), and the printed vs. barcode page number
- green ✓ — every page is right: barcode and printed number both say page *i* of *N* (e.g. `002005` and `2/5`)
- red ✗ — at least one page has a mismatch, a missing barcode, or a missing printed number

Printed numbers are read from the PDF's text; for scanned PDFs without text, only the barcodes are checked.

The page field is the 6 digits (3 for page, 3 for total) located 6 digits before the letter code (`POSTET`) in the barcode data.
Nothing is uploaded; PDF rendering (pdf.js 3.11.174) and barcode decoding (@zxing/library 0.21.3) are vendored in `vendor/`.
