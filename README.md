# WildfireWatch Rwanda

**GitHub:** https://github.com/Shemavainqueur123l3b/shema_20251SEN313_wildfireWatch  
**Student:** Shema Vainqueur | **ID:** 20251SEN313 | **Course:** INSY 8311 (PL/SQL) | **Instructor:** Eric Maniraguha

## Problem statement
Wildfires repeatedly damage Rwanda's forests and parks (for example Nyungwe in 2023 and Akagera in 2012). Satellites detect hotspots, but detections are not stored, linked to a ranger post, or tracked until someone responds, so there is no record of response time, repeat fire locations or unanswered alerts.

## Objectives
**Main:** build an Oracle PL/SQL database that records satellite fire detections for Rwanda and tracks each alert to closure.
**Specific:**
1. Load and validate real NASA FIRMS hotspot data.
2. Score each detection and open alerts automatically.
3. Assign the nearest ranger post and record response time.
4. Report fire frequency by park, district and season.
5. Keep an audit log of every change.

## Data source
NASA FIRMS archive download: MODIS Collection 6 active-fire detections (Terra and Aqua) for Rwanda, CSV, one file per year, 2020-2025 combined (row count to be confirmed after download): https://firms.modaps.eosdis.nasa.gov/. Columns: latitude, longitude, brightness, scan, track, acq_date, acq_time, satellite, instrument, confidence, version, bright_t31, frp, daynight, type. See `data/DATA_NOTES.md`. Acknowledgement text is in `docs/research/research_log.md`. Ranger posts and park boundaries are simulated reference tables built from public park information.

## Innovation
**Smart automation:** a DBMS_SCHEDULER job runs daily, imports new detections, opens alerts via PL/SQL procedures and flags alerts that are still unanswered after a set time.

## Planned tables
DISTRICT, PROTECTED_AREA, RANGER_POST, RANGER, HOTSPOT_DETECTION, FIRE_ALERT, ALERT_RESPONSE, AUDIT_LOG.

## Planned PL/SQL features
- Functions: `calc_risk_level`, `response_minutes`
- Procedures: `open_alert`, `close_alert`, `load_hotspots`
- Cursor: fire count ranking by district, park and season
- Package: `fire_mgmt`
- Triggers: invalid coordinates or confidence; block closing an alert with no response; audit logging
- Exceptions: invalid location, duplicate detection, unassigned post

## Folders
`docs/research/` · `docs/proposal/` · `docs/presentation/` · `data/`

## References
See `docs/research/research_log.md` and the proposal in `docs/proposal/`.
