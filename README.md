# barcode417-check

Local-only page that checks whether the PDF417 barcode on the **last page** of a PDF says "page N of N".

**Live:** https://butra.github.io/barcode417-check/

Open `index.html` in a browser (double-click works, no server needed) and drop a PDF anywhere on the page:

- green ✓ — last page barcode reads e.g. `002002` (page 2 of 2)
- red ✗ — mismatch (e.g. `002000`), no barcode found, or unreadable PDF

The page field is the 6 digits (3 for page, 3 for total) located 6 digits before the letter code (`POSTET`) in the barcode data.
Nothing is uploaded; PDF rendering (pdf.js 3.11.174) and barcode decoding (@zxing/library 0.21.3) are vendored in `vendor/`.
