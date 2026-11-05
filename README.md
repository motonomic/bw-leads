# Enquiry Report Builder

A static web page. Upload the HMSI **Enquiry Detailed Report** (.xlsx, .xls or CSV) and download one Excel file with:

- **Summary** – open enquiries, average follow-ups, no follow-up, overdue next follow-up, invoiced, per sales executive
- **Model Wise** – enquiries for each model by stage (open, booking, invoiced, lost), share, booked or invoiced %, and per executive
- **Open – <executive>** – one sheet per executive: enquiries at Enquiry or Quotation stage, oldest first
- **Invoiced** – invoiced customers in the same format

Several reports (for example October and November) can be added together. They are merged by enquiry number, and the report with the later "data as of" date wins.

Everything runs in the visitor's browser. Report files are never uploaded or stored. There is no server, database or login, and no customer data is kept in this repository.

## Publish on GitHub Pages

1. Create a new repository on GitHub (public is fine, the repository holds only code).
2. Upload all files from this folder to the repository root, including the `vendor` folder and `.nojekyll`.
3. Open **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose branch `main` and folder `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/<repository-name>/`.

To update the page later, replace `index.html` in the repository.

## Notes

- `vendor/` holds the two libraries the page needs (SheetJS 0.18.5 to read reports, ExcelJS 4.4.0 to write the workbook), so the page works without a CDN.
- The page loads IBM Plex fonts from Google Fonts and falls back to system fonts if they are unavailable.
- "Next follow-up date passed" is judged against each report's "data as of" date, which the page takes from the file name and lets you change.
- Open = Enquiry or Quotation stage. Booking and Lost enquiries are left out of the open list.
