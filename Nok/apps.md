<style>
    .markdown-body { max-width: 1500px; } 
    .div-mermaid { max-width: 3000px; }
    .id4 { margin-left: 15px; } 
    .cgray { color: gray; } 
    th {
        background-color: PaleGoldenrod !important;
    }
</style>

# Apps

## <span style='color: gold;'>Road Map</span>

### <font color='gray'>On-hand Project</font>

```mermaid

gantt
title On-hand Projects

dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
axisFormat %d-%b-%y
%%tickInterval 1month

section Pum
    Corp Web: milestone, done, 2023-01-01, 0d
    E-Tax: active, 2023-01-01, 24w
    NEW website/mobile: 2023-08-01, 12w
    
section Yut
    OTA - Migration to MuleSoft: crit, 2023-04-10, 8w
    Web Ticket (Front): active, 2023-04-17, 4w
    
section Tin
    Web Ticket (Back): active, 2023-04-17, 4w
    SCB - Direct Debit: active, 2023-04-27, 4w
    
section Menn
    OTA - Migration to MuleSoft: crit, 2023-04-10, 8w
    OTA - Technical Support: done, 2023-02-01, 26w
    Payment: 2023-06-01, 4w
    ODS Automated: 2023-07-01, 4w
    
section Keaw
    Ticketing: active, 2023-01-15, 4w
    Travel Agencies Portal: done, 2023-02-15, 2w
    Baggage Claim: crit, 2023-04-10, 5w
    Flight Irreg.: k4, 2023-05-08, 4w
    CCM: after k4, 6w
```



### <font color='gray'>Stand Up</font>
```mermaid
gantt
title Stand Up 2023

dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
%%axisFormat %Y-%b
%%axisFormat %a-%d
axisFormat %d-%b-%y
%%tickInterval 1month


section Corp. Web (Pum)
    Implement A: done, 2023-04-10, 1w
    Implement B: crit, 2023-05-10, 1w
    
section e-Tax (Pum)
    Credit Note: 2023-03-01, 9w

section OTA API
    Dev (Mulesoft): 2023-04-03, 8w
    Study Data Models (Yut): 2023-04-26, 1w 

section Payment API
    Kick-off: milestone, active, 2023-06-01, 0d
    
section SCB Direct Debit 
    Kick-off: milestone, done, 2023-04-26, 0d
    Test sandbox (Tin): after s1, 1w

section Web Ticket (Yut, Tin)
    Frontend (Yut): 2023-04-17, 3w
    Backend (Tin): 2023-04-17, 3w
    Go Live: milestone, crit, 2023-05-15, 0d

section Insurance
   Kick-off: milestone, active, 2023-06-01, 0d
   
section ODS Automated
   Kick-off: milestone, active, 2023-07-01, 0d
   
section NEW Web/Mobile
   Kick-off (Pum): milestone, active, 2023-08-01, 0d
```


### <font color='gray'>Currently</font>
```mermaid
gantt
title Development Plan 2023

dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
%%axisFormat %Y-%b
%%axisFormat %a-%d
axisFormat %b
%%tickInterval 1month

section CMDB
    1st Mockup: done, milestone, 2022-12-15, 1d
    Import existing data: crit, 2023-04-21, 3d
    Modify some fields: 2023-04-24, 1w 

section e-Tax (Pum)
One Payment: done, e1, 2023-01-01, 4w
Cancel: done, e2, after e1, 4w
Credit Note: crit, e3, after e2, 4w
Go Live: milestone, active, after e3, 0d
Split Flight: e4, after e3, 6w
Split Passenger: e5, after e4, 4w

section OTA API (Re-code)
    Kris version support: o1, 2023-01-15, 8w
    De-code SOAP: o2, 2023-02-01, 8w
    Urgently re-code API for OTA (India): o6, 2023-02-10, 4w
    Re-code & adjust API functions: crit, o7, 2023-02-15, 20w
    Fare Type: o3, after o2, 4w
    Study SSR and other services: o8, 2023-04-01, 8w
    API document and Swagger: o5, 2023-04-01, 8w
    Booking (re-code): o4, after o3, 4w
    SSR: o5, after o4, 4w
    Cooperate with Partner to Implement Nok Air's Middleware: o9, 2023-04-15, 12w
    
section Navision
   Kick-off: milestone, active, 2023-03-01, 0d
   Technical Support: n1, 2023-01-01, 16w
   Data Interface (Pause): n2, 2023-04-01, 4w
   Bank Text File (Pause): n3, 2023-04-01, 4w
   Plan to change the system: milestone, n4, 2023-03-15, 1d
   Migration Solution: n5, 2023-05-09, 1d

section CRM (CCM)
   Kick-off: milestone, active, 2023-02-15, 0d
   Implement: crit, 2023-04-17, 6w


section Voucher Control
   Kick-off: milestone, active, 2023-02-20, 0d
   Implement: crit, 2023-03-28, 6w


section Insurance
   Kick-off: milestone, active, 2023-03-15, 0d

section MuleSoft
   API workshop: w1, 2023-03-27, 3d
   Setup: crit, e1, 2023-04-03, 4w
   Implement: active, i0, 2023-05-01, 24w

section Payment API
Kick-off: milestone, active, 2023-04-01, 0d
```


### Links
1. [CCM](https://hackmd.io/t-Ilc3ssSCmkTCgQ_Iy8ew#Timeline)
1. [E-Tax](https://dev.azure.com/NokDevOps/e-Tax/_wiki/wikis/e-Tax.wiki/200/Timeline)
1. [MuleSoft](https://dev.azure.com/NokDevOps/MuleSoft/_wiki/wikis/MuleSoft.wiki/166/Timeline)
1. [Payment](https://dev.azure.com/NokDevOps/Nok%20Pay2/_wiki/wikis/Nok-Pay2.wiki/73/QR-Payment)
1. [Ticketing](https://hackmd.io/bman_puCTu2z9DhZNIjT6w?view)