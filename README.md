WildfireWatch Rwanda

Satellite Fire Hotspot Monitoring and Ranger Response Database

	
Student	Shema Vainqueur
Student ID	20251SEN313
Course	INSY 8311 (PL/SQL)
Instructor	Eric Maniraguha
GitHub	https://github.com/Shemavainqueur123l3b/shema_20251SEN313_wildfireWatch
Current phase	Phase 0: research, data source and proposal
Problem statement

Wildfires repeatedly damage Rwanda's forests and parks (for example Nyungwe in 2023 and Akagera in 2012). Satellites detect hotspots, but the detections are not stored, linked to a ranger post, or tracked until someone responds. As a result there is no record of response time, repeat fire locations or unanswered alerts.

Objectives

Main objective: build an Oracle PL/SQL database that records satellite fire detections for Rwanda and tracks each alert to closure.

Specific objectives

Load and validate real NASA FIRMS hotspot data.
Score each detection and open alerts automatically.
Assign the nearest ranger post and record response time.
Report fire frequency by park, district and season.
Keep an audit log of every change.
Data source
NASA FIRMS archive download: https://firms.modaps.eosdis.nasa.gov/
MODIS Collection 6 active-fire detections (Terra and Aqua, 1 km) for Rwanda, CSV format.
Yearly files for 2020-2025 will be combined. Row count: to be confirmed after download.
Columns: latitude, longitude, brightness, scan, track, acq_date, acq_time, satellite, instrument, confidence, version, bright_t31, frp, daynight, type.
Free to download; NASA asks users to acknowledge FIRMS. The data contain no personal information.
Simulated data: ranger posts and park boundaries are reference tables I build from public park information. They are not real operational data.
Data checks and notes: see data/DATA_NOTES.md.
Innovation

Option: Smart automation. Tool: DBMS_SCHEDULER. A daily job imports new detections, opens alerts by calling the PL/SQL procedures, and flags alerts still unanswered after a set time. Business rules stay in PL/SQL; the job only calls them. It will be demonstrated live in Phase VII.

Planned tables
Table	Purpose
DISTRICT	Rwanda districts
PROTECTED_AREA	Parks and forests
RANGER_POST	Posts used for nearest-post assignment
RANGER	Staff at each post
HOTSPOT_DETECTION	Loaded FIRMS detections
FIRE_ALERT	Alert per fire, with risk level and status
ALERT_RESPONSE	Assigned post, arrival time, outcome
AUDIT_LOG	Record of every change

A district or park has many hotspots; a hotspot may open one alert; an alert has one or more responses. The design will be normalised to 3NF in Phase II.

Planned PL/SQL features
Feature	Where it is used
Functions calc_risk_level, response_minutes	Score a detection; compute minutes from alert to arrival
Procedures open_alert, close_alert, load_hotspots	Create an alert and assign the nearest post; record the outcome; validate and insert detections
Cursor	Rank districts and parks by fire count per season
Package fire_mgmt	Groups all of the logic
Triggers	Reject invalid coordinates or confidence; block closing an alert with no response; write changes to AUDIT_LOG
Exceptions	Invalid location, duplicate detection, unassigned post
Repository structure
README.md
data/                  FIRMS CSV files and DATA_NOTES.md
docs/research/         research_log.md
docs/proposal/         WildfireWatch_Rwanda_Proposal.docx
docs/presentation/     WildfireWatch_Rwanda_Presentation.pptx

More folders are added in later phases.

References

Giglio, L., Schroeder, W., & Justice, C. O. (2016). The Collection 6 MODIS active fire detection algorithm and fire products. Remote Sensing of Environment, 178, 31-41. https://doi.org/10.1016/j.rse.2016.02.054

Musabwa, F., & Mukeshimana, M. C. (2026). Assessing forest landscape dynamics and its driving factors in Rwanda, a case of Nyungwe National Park (1990-2024). East African Journal of Environment and Natural Resources, 9(2), 110-127. https://doi.org/10.37284/eajenr.9.2.4904

NASA. (n.d.). Fire Information for Resource Management System (FIRMS). https://firms.modaps.eosdis.nasa.gov/

Oracle. (n.d.). DBMS_SCHEDULER. In Oracle Database PL/SQL Packages and Types Reference. https://docs.oracle.com/cd/E24693_01/appdev.11203/e23448/d_sched.htm

The New Times. (2012, August 30). Fire guts 20pc of Akagera Park. https://www.newtimes.co.rw/article/79108/National/fire-guts-20pc-of-akagera-park

The New Times. (2023). Wildfire guts parts of Nyungwe forest. https://www.newtimes.co.rw/article/10122/news/wildfire-guts-parts-of-nyungwe-forest

Full source list with key findings and gaps: docs/research/research_log.md.

Data acknowledgement: we acknowledge the use of data and imagery from NASA's Fire Information for Resource Management System (FIRMS), part of NASA's Earth Science Data and Information System (ESDIS).
