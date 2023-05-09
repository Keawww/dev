<style>
    .markdown-body { max-width: 1500px; } 
    .div-mermaid { max-width: 3000px; }
    .id4 { margin-left: 15px; } 
    .cgray { color: gray; } 
    th {
        background-color: PaleGoldenrod !important;
    }
</style>

# MuleSoft


```mermaid
gantt
title MuleSoft Implementation (Overview)
dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
axisFormat %b-%y
%%tickInterval 1month

section Paper Work
   Signed back quotation: done, p1, 2023-03-15, 1h
   Revised v1 agreement: done, p2, 2023-03-21, 1h
   Revised v2 agreement: crit, p2, 023-04-19, 4h

section Workshop
   API workshop: done, w1, 2023-03-27, 3d

section Environment Setup
   Setup Meeting (X10): done, e0, 2023-04-05, 1d
   Platform Setup (Delay): done, e1, after e0, 4w
   Platform Setup: crit, e2, after e1, 2w

section OTA-SSR (Transformation)
   Get requirement: done, ot1, 2023-04-11, 1w
   SSR review (Delay): done, 2023-04-25, 2d 
   SSR review: crit, 2023-05-08, 2d 
   Review & Sign-off (Delay): done, ot2, after ot1, 1w
   Review & Sign-off: ot2, 2023-05-10, 1w
   Development (Delay): done, ot3, 2023-04-25, 4w
   Development: crit, ot31, 2023-05-08, 4w
   Test case, SIT, UAT, sign off: ot4, after ot31, 1w
   Cut over, Go Live, Sign off: ot5, after ot4, 1w

section Payment (Transformation)
   QR:  2023-06-01, 4w
   SCB (Direct):  2023-06-10, 4w

section Insurance
   Implementation:  i3, 2023-07-01, 4w
   
section Irregularity handling
   Irregularity handling:  i4, after i3, 4w
   
section Corp Web
   Corp Web:  i5, after i4, 6w
   
section Mobile app
   Mobile app:  i6, after i5, 4w
   
```