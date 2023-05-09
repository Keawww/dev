<style>
    .markdown-body { max-width: 1500px; }
    .div-mermaid { max-width: 3000px; }
    .st-blue { color: dodgerblue; font-size: 0.8em; }
    .st-green { color: green; font-size: 0.7em; }
    .st-red { color: darkred; font-size: 0.7em; }
    .st-orange { color: salmon; font-size: 0.7em; }
</style>

# Navision

[toc]

# Meeting
## Exsys
- Migration Solution `09may23`
    - Company Profile
    - Service
    - Nok Information
        - NAV2017
            - 53 concurrent users
            - 1 Application bulider
        - Dynamic 365
    - Solution by Exsys

# Contract
```mermaid
gantt
title Navision - Exsys
dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
axisFormat %b-%y
%%tickInterval 1month

section Contract
    2022 MA: milestone, done, 2022-06-25, 0d
    2023 MA: milestone, active, 2023-06-25, 0d
    
section Navision Implementaion
    Migration Solution: active, 2023-05-09, 1d
```