# Data notes

**Source:** NASA FIRMS archive download, MODIS active fire detections, Rwanda. Put the CSV files in this folder (for example `firms_modis_rwanda_2025.csv`).

**Columns:** latitude, longitude, brightness, scan, track, acq_date, acq_time, satellite, instrument, confidence, version, bright_t31, frp, daynight, type

## Checks to do in Phase II/IV
- `acq_time` is a 4-digit text value (for example `1220` = 12:20); convert when loading.
- `confidence` is numeric 0-100 for MODIS. Test rows exist with confidence 0 but high `frp` (for example 2025-07-17, -1.5131, 30.4176).
- `type` is 0 for most rows; some rows have `type = 2` (check the FIRMS MODIS documentation for the meaning before using it).
- Many detections on one day close together (for example 2025-08-05, about 07:15) are probably one fire seen as several pixels; group nearby same-day detections into one alert.
- The CSV has no district, park or ranger post; those are separate reference tables.
