The app is live here:

https://msd3sign.github.io/packet-check-time-analyzer/

# Packet Check Time Analyzer — v3.0

## What changed in this version (v3.0)

**New Departamento column in the Seasonal Schedule List, plus security, printing and validation hardening:**

- New **Departamento** column between Associate Name and Associate # in the Seasonal Schedule List, taken from the report's `AREA: #### - Name` section lines. It shows only the area name, without the number. Seasonal associates listed before any AREA line keep an empty Departamento, and the AREA lines still count as ignored lines, so the report diagnostics do not change.
- **Security:** all rendered report data is now HTML-escaped, and the print flow checks that the print window opened successfully before building the document.
- **Printing:** the printed sheet now respects BOTH on-screen filters — the package check quantity selector and the "Show only seasonals" checkbox (v2.8.5 ignored the checkbox and printed everything). If no rows are visible, it warns instead of printing an empty sheet. The print document is now built with DOM methods instead of `document.write`. With the default filters and with Top 5, the printed sheet is identical to v2.8.5, including the "Day:" / "Date:" footer, which always uses the date from the pasted report's header, never today's date.
- **Validation:** pasted text that does not look like an Area Walk Report is rejected with a warning. The report header date is verified as a real calendar date whose weekday matches the header. Time values are range-checked (hour 1–12, minutes 0–59), and lines with missing scheduled hours are counted as invalid instead of being silently treated as 0.
- **Diagnostics:** after processing a report, a summary now shows Lines processed / Ignored / Invalid, and warns when the report date header was not detected or is inconsistent (printing then falls back to today's date).
- **Cleanup:** removed dead code, including the old commented-out print function. No other behavior changed.

---

## What changed in this version (v2.8.5)

- The printed sheet's "Date:" field now uses the date from the pasted report's header ("Area Walk Report for: ...") instead of today's date, so reports from other days can be analyzed. The "Day:" field is calculated from that same date, so Day and Date always match.

---

## What changed in this version (v2.8.4)

- Filtering the "Associates by Hour" chart now keeps its height, bar thickness and vertical scale, calculated from the full (unfiltered) data.

---

## What changed in this version (v2.8.3)

- Modules: Import Walk Report, Walk Report by 30 min, Associates by Hour and Seasonal Schedule List.
- Conditional print button.
- Reorganized filters and seasonal list.

---

## What it does

- Paste the full content of the Area Walk Report.
- Generates the "Walk Report by 30 min" table (Schedule Out / Meal Out / Total), marking in parentheses how many of each count are Seasonals.
- "Show only seasonals" checkbox next to the filter, to show only the times that have at least one Seasonal.
- Seasonal Schedule List module: associate name, department, associate number and schedule for every Seasonal found in the report.
- Dashboard with an associates-by-hour chart, with its own checkbox to sync (or not) with the table filter.
- Filter by the number of package checks for the day.
- Printable sheet, ready to fill in on the floor.

## Local use

Open `index.html` in any browser — no server or build required.

## Online use (GitHub Pages)

Once this repo is on GitHub:

1. Go to **Settings → Pages**.
2. Under "Build and deployment" → Source, choose **Deploy from a branch**.
3. Branch: `main`, folder `/ (root)` → **Save**.
4. Within a couple of minutes the app will be available at:
   `https://YOUR_USERNAME.github.io/REPO_NAME/`
