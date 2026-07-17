# XER Timeline Builder

A single-file web app that builds a **one-page project timeline PDF** from an
**XER schedule export**: summary bars per WBS phase, milestone callouts,
progress shading and a classic print-style header and footer — all
configurable in the sidebar, with a live preview.

The entire app is the one `index.html` in this repository. Host it on any
static web server (GitHub Pages works out of the box) or open it directly
from disk in a modern browser.

## Privacy

Your schedule data **never leaves your machine**. The app runs entirely in
the browser: Python compiled to WebAssembly renders the PDF locally, and the
hosting server only ever delivers the app shell.

Clicking **Initialise** downloads the runtime components (~15 MB) from
`cdn.jsdelivr.net`, `pypi.org` and `files.pythonhosted.org` — an internet
connection is required for that first step and those hosts must be reachable
through your proxy/firewall. The download is cached by the browser.
**After initialisation no further network connection is made.**

## Usage

1. Open the page and click **Initialise**.
2. Upload an `.xer` schedule export.
3. Adjust in the sidebar: WBS summarization depth, milestone selection
   (auto-capped, hand-picked from a list, all, or none), bar coloring by
   activity code, progress shading, paper size, title, project ID, company,
   logo and the schedule-revisions table.
4. The preview re-renders on every change; **Download PDF** saves the result.
5. **Save settings (.json)** captures every option — including the uploaded
   logo — per project; load the file back next time instead of re-typing.

## Requirements

A modern desktop browser (tested in Edge and Chrome). Internet access is
needed only for the first initialisation per browser.

## Third-party components

- **DejaVu fonts** are embedded in `index.html` for PDF text rendering,
  redistributed under the
  [DejaVu Fonts License](https://dejavu-fonts.github.io/License.html).
- The Python runtime and libraries (stlite, Pyodide, Streamlit, reportlab)
  and the pdf.js preview renderer are **fetched from their public CDNs at
  initialisation**, not redistributed here.
