# Research Log: WildfireWatch Rwanda



|#|Source (APA)|Type|Link|Key finding|Gap it shows|
|-|-|-|-|-|-|
|1|Musabwa, F., \& Mukeshimana, M. C. (2026). Assessing forest landscape dynamics and its driving factors in Rwanda, a case of Nyungwe National Park (1990–2024). *East African Journal of Environment and Natural Resources, 9*(2), 110–127.|Research paper|https://doi.org/10.37284/eajenr.9.2.4904|Landsat analysis of Nyungwe shows that fire disturbance, along with farming and roads, changes vegetation and can start cycles of forest-to-grassland conversion.|Studies map land cover change from imagery but do not give managers an operational record of fire alerts and responses.|
|2|Giglio, L., Schroeder, W., \& Justice, C. O. (2016). The Collection 6 MODIS active fire detection algorithm and fire products. *Remote Sensing of Environment, 178*, 31–41.|Research paper|https://doi.org/10.1016/j.rse.2016.02.054|Collection 6 improved MODIS fire detection: global commission error of the daytime Terra product fell to 1.2% from 2.4% in Collection 5, with fewer false alarms from small forest clearings.|The paper covers detection quality, not what a park authority does after a detection.|
|3|The New Times. (2023). Wildfire guts parts of Nyungwe forest.|Report / news|https://www.newtimes.co.rw/article/10122/news/wildfire-guts-parts-of-nyungwe-forest|A fire in Bweyeye Sector, Rusizi District burned over 8 ha; the manager said earlier fires were often linked to illegal honey harvesting; the law allows up to five years' prison and a Rwf3 million fine.|Damage is estimated after the fire; no system links detections, response time and cause.|
|4|The New Times. (2012, August 30). Fire guts 20pc of Akagera Park.|Report / statistic|https://www.newtimes.co.rw/article/79108/National/fire-guts-20pc-of-akagera-park|An estimated 20% of Akagera National Park (1,121.93 km²) burned in August 2012; several fires started on different dates.|Several fires over weeks show the need to track each detection and response separately.|
|5|NASA. (n.d.). Fire Information for Resource Management System (FIRMS).|Existing system|https://firms.modaps.eosdis.nasa.gov/|FIRMS gives free near-real-time and archive MODIS/VIIRS hotspot data, map viewing and email alerts by area.|FIRMS shows detections but does not record who responded, response time or alert closure, and has no Rwandan ranger-post workflow.|
|6|NASA. (n.d.). FIRMS archive download: MODIS active fire detections, Rwanda (CSV).|Dataset|https://firms.modaps.eosdis.nasa.gov/|Country-level CSV of MODIS (Terra/Aqua) detections with latitude, longitude, brightness, date, time, confidence and FRP. My 2025 file has about 135 rows; years 2020–2025 will be combined.|Raw CSV is not a validated relational database with business rules.|
|7|Oracle. (n.d.). DBMS\_SCHEDULER. In *Oracle Database PL/SQL Packages and Types Reference*.|Technical source|https://docs.oracle.com/cd/E24693\_01/appdev.11203/e23448/d\_sched.htm|DBMS\_SCHEDULER can run stored procedures or PL/SQL blocks on a repeat interval (e.g. `FREQ=DAILY;BYHOUR=12`).|Shows the scheduling tool for the daily import-and-alert job; the fire rules still have to be written in PL/SQL.|

## Acknowledgement text required by NASA

"We acknowledge the use of data and/or imagery from NASA's Fire Information for Resource Management System (FIRMS) (https://earthdata.nasa.gov/firms), part of NASA's Earth Observing System Data and Information System (EOSDIS)."

## 

