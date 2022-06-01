---
description: >-
  The APU APS5000 constants defaults are presented below. If there is a need to
  change the value of any constant - go to General Admin -> Constants.
---

# B787 constants

| Constants Name                        | Description                                                                                                                                                        | Value |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- |
| HMS\_APS5000\_LIMIT\_OIL\_DP          | <p></p><ul><li>value in psid</li></ul><ul><li>limit for Main Oil delta pressure used in calculation of predictive alert for oil delta pressure at REP202</li></ul> | 40    |
| HMS\_APS5000\_LIMIT\_GEN\_OIL\_DP     | <ul><li>threshold used at DB aps5000 cross section (GenDP_anim)</li></ul>                                                                                          | 20    |
| HMS\_APS5000\_LIMIT\_PEAK\_EGT\_DELTA | <ul><li>threshold used at DB aps5000 cross section (EGTsensor_anim)</li></ul>                                                                                      | 79.5  |
| HMS\_APS5000\_LIMIT\_REP202\_NO\_DATA | <ul><li>value in DAYS</li></ul><ul><li>threshold used at layout OOOI-off</li><li>send indication that APU is not sending data.</li></ul>                           | 2     |
| HMS\_APS5000\_THRESHOLD\_REFILL\_OIL  | <ul><li>value in quarters</li><li>refill threshold used in calculation of predictive alert for oil consumption at REP202</li></ul>                                 | 0.5   |
| HMS\_APS5000\_LIMIT\_TIME\_RTL        | <ul><li>value in seconds</li><li>time ready to load threshold used in calculation of predictive alert for time ready to load at REP202</li></ul>                   | 50    |
| HMS\_APS5000\_LIMIT\_DOOR\_CL\_TIME   | <p></p><ul><li>value in seconds</li></ul><ul><li>Door Closing Time limit is used in calculation of predictive alert for DOOR_CL_TIME at REP202</li></ul>           | 34    |
| ADMIN                                 | <ul><li>value in ["email1"]</li></ul>                                                                                                                              |       |
| REVIMA                                | <ul><li>value in ["email1", "email2"]</li></ul>                                                                                                                    |       |
| CLIENT\_ENG                           | <ul><li>value in ["email1", "email2"]</li><li>HMS APU Power Plant engineers to be alerted</li></ul>                                                                |       |
| CLIENT\_MCC                           | <ul><li>value in ["email1", "email2"]</li><li>HMS APU Maintenance Control Center Engineers to be alerted</li></ul>                                                 |       |
