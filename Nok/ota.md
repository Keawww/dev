<style>
    .markdown-body { max-width: 1500px; }
    .div-mermaid { max-width: 3000px; }
    .st-blue { color: dodgerblue; font-size: 0.8em; }
    .st-green { color: green; font-size: 0.7em; }
    .st-red { color: darkred; font-size: 0.7em; }
    .st-orange { color: salmon; font-size: 0.7em; }
</style>

# OTA

[toc]

---



# Go Live Timeline
```mermaid
gantt
title Travel Agency Go Live
dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
axisFormat %b-%y
%%tickInterval 1month

section Go Live
    Ease My Trip: milestone, done, 2023-04-10, 0d
    Mystifly: milestone, done, 2022-08-15, 0d
    Ningbo Qihang (Reactivate): milestone, active, 2023-04-30, 0d
    TBO: milestone, done, 2023-03-15, 0d
    Tianshiyuan: milestone, done, 2023-04-01, 0d
    TravelFusion: milestone, done, 2022-08-15, 0d
    Trip.com (Connected TravelFusion): milestone, done, 2023-04-01, 0d
section Pre-Go Live
    Alhind: milestone, crit, 2023-04-30, 0d
    Beijing New Sun: milestone, active, 2023-05-16, 0d
    Chongqing Wangyi: milestone, crit, 2023-04-30, 0d
    Goomoo India: milestone, crit, 2023-04-30, 0d
    Riya: milestone, crit, 2023-04-30, 0d
    Alhind: milestone, crit, 2023-04-30, 0d
section API Testing
    FairFair: milestone, active, 2023-06-01, 0d
    TripJack: milestone, active, 2023-05-31, 0d
    TripStack: milestone, active, 2023-05-15, 0d
section NDA Phase
    Guangzhou Jinxiangda: crit, 2023-04-28, 1w
```


# Features
## Existing OTA API
```mermaid
graph LR

1([getAvaliability])
2([pricing])
3([sell])
31([clearSession])
4([updatePassenger])
5([submitHoldBooking])
6([getBookingFromSellKey])
7([getPaymentAccount])
8([Confirm])
9([getBooking])

1 -->|1| 2
2 -->|2| 3 -->|??| 31
31 -->|??| 1
3 -->|3| 4
4 -->|4| 5
5 -->|5| 6
6 -->|6| 7
7 -->|7| 8
8 -->|8| 9
```


## New OTA API
```mermaid
graph LR

0((Start))
0a((X))
1([getAvaliabilityFlightFare])
2([getPricingDetailSSR])
3([getSSR])
31[getBaggage]
32[getMeal]
33[getSeat]
34[getInfant]
4([getSeatMap])
5([submitHoldBooking])
6([confirm])
7([getBooking])
8([getAccountBalnce])

0 --> 1
0 --> 8
1 --> |1| 2
2 --> |2| 5
2 -.-> |2a| 3
2 -.-> |2b| 4
5 --> |4| 6
4 -.-> 5
6 --> |5| 7

3 -.-> 31 -.-> 0a
3 -.-> 32 -.-> 0a
3 -.-> 33 -.-> 0a
3 -.-> 34 -.-> 0a
0a -.-> 5

classDef system color: gray, fill: lightyellow, stroke: gray, stroke-dasharray: 3 3
classDef connector color: gray, fill: gainsboro, stroke: gray, stroke-dasharray: 2 2
class 31,32,33,34 system
class 0a connector

```

## _Booking Flow_
1. Initiate the "GetAvailability" API call to retrieve flight availability information.
1. Use the "Pricing" API to calculate the fare and journey details.
1. Submit a "Sell" API call to confirm the booking.
1. Update passenger information using the "UpdatePassenger" API call with the SellKey.
1. Hold the booking with the "SubmitHoldBooking" API call using the SellKey.

Is this booking flow correct or are there any necessary changes that need to be made?