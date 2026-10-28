# barcode417-check

Local-only page that shows and decodes the PDF417 barcode on **every page** of a PDF, and checks each one against the page number printed at the bottom (e.g. `2/5`).

**Live:** https://butra.github.io/barcode417-check/

Open `index.html` in a browser (double-click works, no server needed) and drop a PDF anywhere on the page:

- each page gets a card with the barcode image, the decoded text (page field highlighted), the printed page number, and the expected vs. actual code
- green ✓ — every page's barcode code matches its printed number `n/a`: `00n000` on every page except the last, `00n00a` on the last page (n = a)
  - e.g. 1/1 → `001001`; 1/2 → `001000`, 2/2 → `002002`
- red ✗ — at least one page has the wrong code, no barcode, or no printed number

Printed numbers are read from the PDF's text; for scanned PDFs without text, the page order in the PDF is used instead.

The page field is 6 digits at a fixed position: characters 56–61 of the barcode text, counting from 1 (3 digits for the page, then 3 for the total or `000`). Change `PAGE_FIELD_START` in `index.html` if that position ever moves.
Nothing is uploaded; PDF rendering (pdf.js 3.11.174) and barcode decoding (@zxing/library 0.21.3) are vendored in `vendor/`.
