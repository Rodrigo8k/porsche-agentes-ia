# Porsche Sales Intelligence Dashboard - Agent Guidance

## Overview
- Single-file HTML dashboard with embedded data, no build step.
- Open in any modern browser to use; no server required.
- Uses Chart.js v4.4.7 from CDN; offline use fails gracefully (KPIs/table still work).

## Data
- Data is hardcoded in `rawData` array (see `<script>` top).
- Source Excel (planilha de origem, fora do repositório) is for reference only; not read at runtime.
- To update data: edit the `rawData` array (must be valid JSON array of objects).
- Each object must have sanitized fields: `PorscheModelSanitized`, `ModelYearSanitized`, `SalesPriceSanitized`, `PayMethodSanitized`, `CitySanitized`, `StateSanitized`.

## Development
- No dependencies; edit HTML/CSS/JS directly.
- Hero background images: edit `heroPhotos` array (Unsplash URLs) to rotate different images.
- Chart colors: modify `getColorForPayMethod` or chart-specific color arguments.
- To add/remove filters: update `populateSelect` calls and filter logic in `updateDashboard`.
- Export functions:
  - `exportFilteredCSV()`: downloads filtered data as CSV.
  - `exportChartAsPNG()`: downloads yearly revenue chart as PNG (fixed chart).
- Reset filters: `resetFilters()` sets all selects to "All".

## Testing
- No automated tests; manual verification:
  1. Change filter selections; confirm KPIs/charts update.
  2. Test export buttons produce downloadable files.
  3. Resize browser; verify responsive layout.
  4. Disable internet; confirm Chart.js error shows but KPIs/table still render.
  5. Check console for errors when modifying data format.

## Gotchas
- Data array must remain valid JSON; trailing commas or missing quotes break JS.
- Field names in filters (`populateSelect`) must match rawData keys exactly.
- Chart.js version is pinned; updating CDN link may require adjustments.
- Hero images load from external URLs; if blocked, slideshow shows blank (but no error).
- File size grows with data; for >1k records consider external data fetch (not current setup).