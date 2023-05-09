<style>
    /*
    html, body, .ui-content {
        background-color: black;
        color: lightgray;
    }
    */
    .markdown-body { max-width: 1500px; }
    .div-mermaid { max-width: 3000px; }
</style>

:::info
:information_source: [Apps](https://hackmd.io/pePD1kwgRfyckzzAPIBRxw#Apps)
:::

# CCM

[toc]

# Timeline
```mermaid
gantt
title CCM Apps
dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
%%axisFormat %Y-%b-%a-%d
axisFormat %d-%b-%y
%%tickInterval 1month

section Process
   Irreg. process: p1, 2023-03-31, 1h


section Compensation
   Initial app: d1, 2023-03-31, 2h
   Excel Import: d2, 2023-04-02, 1w
   Manage compensate page: crit, d5, 2023-04-06, 4d
   Import Validation: d3, 2023-04-10, 3d
   Email voucher to Pax: d4, after d3, 1w
   1st mock up: crit, milestone, 2023-04-17, 2h
   Voucher report: d6, 2023-04-17, 1w
   
section Baggage Claims
   Import voucher: 2023-04-21, 1w 
   Request Claim: crit, 2023-04-27, 3d
   Email voucher: 2023-05-02, 2d 
   1st mock up: crit, milestone, 2023-05-10, 2h


section Meeting
   Voucher review with Som: 2023-04-04, 2h

```



# Baggage Claims

## Overview

1. ผู้โดยสารทราบกระเป๋ามีปัญหา เช่น แตก หัก ชำรุด เป็นต้น (ที่สนามบินต้นทางหรือปลายทาง)
1. ผู้โดยสารติดต่อที่สนามบินปลายทาง
1. เจ้าหน้าที่ประเมินค่าเสียหาย โดยจ่ายเป็น Voucher มูลค่า 500 หรือ 1,000 บาท รวมมูลค่าไม่เกิน xxxx บาท
1. เจ้าหน้าที่ดำเนินการเตรียมเอกสารดังนี้
    - Passenger  Baggage Claim Form
    - Property Irregularity Report (PIR)
    - ใบรับเงิน
    - ถ่ายสำเนาบัตรประชาชน หรือ passport ผู้โดยสาร
1. เดิม จ่ายเป็นสด เปลี่ยนเป็น Voucher
    - โดยทาง CIC จะ generate Voucher มูลค่า 500 บาท และ 1,000 บาท อย่างละ 1,000 ใบ อายุ 1 ปีนับจากวันที่ gen voucher
    - ทางสถานีจัดเตรียมเอกสารตามข้อ 4
    - เปลี่ยนจากการเขียนเอกสารใบรับเงิน เป็นเจ้าหน้าที่กรอกรายละเอีดยลงในระบบ > เลือก Compensate 500บาท หรือ 1,000 บาท จำนวน x ใบ > ปริ้นเอกสารให้ผู้โดยสารเซ็นต์
        - หมายเหตุ สำหรับแบบฟอร์มใบรับเงินขอสอบถามหน่วยงานที่เกี่ยวข้องก่อนนะคะ
        
## Tasks
```mermaid
gantt
title Baggage Claim Tasks
dateFormat YYYY-MM-DD
todayMarker stroke:#ADFF2F, opacity:0.7
axisFormat %d-%b
%%tickInterval 1month

section Claim Form
    Request claim: active, 2023-04-17, 2w
    Dispense voucher: crit, c2, 2023-04-28, 1d
    Email to Pax: active, c3, after c2, 1d
    
section Reports
    Voucher dispensed: active, r1, after c3, 1d
    
UAT 1: milestone, u1, after r1, 0d
Go Live: crit, milestone, after u1, 0d
```



## Workflow
```mermaid
graph

subgraph Apps
   v((Voucher)) --> m[[Email]]
end

subgraph Pax
   r([Request Claim])
   ref[[Reference Doc]]
   s["<img src='https://img.icons8.com/ios-filled/512/autograph.png' width='32'>"]
   %%vc["<img src='https://img.icons8.com/ios-filled/512/loyalty-card.png' width='32'>"]
   vc["<img src='https://img.icons8.com/ios-filled/512/membership-card.png' width='32'>"]
   m -.-> |voucher| vc
end

subgraph Station/NokContact
   r --> |1| rd{Rate Damage}
   ref --> |2| d --> v
   s --> |3| d
   rd --> |Y| d(Prepare document)
   rd --> |N| j([Rejected])
end

subgraph CIC
   gv(Generate) -.-> v
end


linkStyle default stroke: silver, fill: transparent
classDef black stroke: gray, stroke-width:3px;
classDef notdone stroke: darkred, stroke-width:2px;
classDef orange color: orange, stroke: orange, stroke-width:1px;
classDef tpr fill: transparent, stroke: lightgray, stroke-width: 1px;
classDef gtpr fill: ghostwhite, stroke: lavender, stroke-width: 1px;
class j black
%%class rd orange
class s tpr
class Apps,Pax,Station/NokContact,CIC gtpr
class r,m,gv,v,vc,rd notdone

```



# Flight Irreg.

## Overview
``` mermaid
graph TD

st([Station]) --> a
a[Import Excel] -->|1| b((Apps))
b -..->|2. Process| b
b -->|3| c[[Email voucher]]

d[(Voucher)] -..-|Update| b
c --> p([Pax])
d --> vr[[Voucher Report]]
```

## Compensation / Import
```mermaid
sequenceDiagram

title Flight Irreg. (Compensation / Import)
autonumber
participant op as OP
participant s as Station
participant a as Apps
participant go as GO
participant ns as NokSmart


op ->> s: Announce OP/ASM Code by mail
ns -->> s: Query data (every 2AM.)
go -->> s: Query data (per request)
s ->> a: Import Excel
```




# ^C^ompensation
```mermaid
graph TB

subgraph GO
   paxgo[(Pax Info)]
end

subgraph Insight
   paxin[(Pax Info)]
end

subgraph OP
   an(Announce)
end

subgraph NokSmart
   paxns[(Pax Info)]
end

subgraph Station
    an --> |1. Announce OP/ASM Code by mail| im(Import)
    v(Verify)
    apv(Approved)
    paxns --> |2. Report from 2AM| im
    paxgo --> |3. Report per request| im
    paxin --> |4. Report??| im
end

subgraph DB
  %% vc -.-> vdb[(Voucher)]
  vdb[(Voucher)]
end

subgraph Apps
   v --> |-2-| q((Query Pax))
   q -.-> |-3-| v
   vc((Voucher)) -.-> vdb
   rp((Reports))
   pax((Pax Info))
   im --> |5. Excel| pax
   apv --> |-4-| vc
end

subgraph Accounting
    rp -.-> ar[[Reports]]
end

subgraph Pax
   r([Request<br>Compensation]) --> |-1-| v
   vcid[[Voucher]]
   vc -.-> |-5- email| vcid
end

```




## ^R^equirement

### In case of flight irregularity

1. เมื่อมีประกาศ Flight IRR เจ้าหน้าที่ีที่ update flight status หรือเจ้าหน้าที่ที่เกี่ยวข้องสามารถดำเนินการดังนี้
- จัดส่ง SMS
- จัดส่ง E-mail
- เลือก Option การช่วยเหลือผู้โดยสารตามเงื่อนไข CAAT ได้แก่
   - เปลี่ยนแปลงเที่ยวบินฟรี 1  ครั้ง
   - เก็บเครดิต 100% ระยะเวลา xx เดือน > ระบบ generate และส่งอีเมลแจ้งผู้โดยสาร พร้อมเงื่อนไข
   - เปลี่ยนแปลงเส้นทาง
   - คืนเงิน

1. ระบบตรวจสอบว่าชำระเงินรูปแบบไหน
   - Cash ระบบให้กรอกเลขที่บัญชี ชื่อบัญชี ธนาคาร หากโอนให้บุคคลอื่น ให้แนบเอกสารได้
   - บัตรเครดิต
   - ซื้อผ่านตัวแทนจำหน่าย > ระบบแจ้งติดต่อผ่านตัวแทนฯ ภายใน 45 วันทำการ

1. เมื่อผู้โดยสารกรอกรายละเอียดเรียบร้อยส่งไปที่บัญชี
1. บัญชีดำเนินการคืนเงิน
1. การเงินส่งเรื่องให้ธนาคารเพื่อคืนเงินแต่ละช่องทาง
1. การเงิน update status การคืนเงิน
1. ระบบส่ง SMS/E-mail ให้ผู้โดยสารเมื่อคืนเงินเรียบร้อย
1. ระบบลงบันทึก
   ได้รับเงินชดเชย 600 บาท หรือ 1,200 บาท (ระบบสามารถเลือกได้)
   - เงินสด กรอกเลขที่บัญชี ชื่อบัญชี ธนาคาร หากโอนให้บุคคลอื่น ให้แนบเอกสารได้
   - เมื่อผู้โดยสารกรอกรายละเอียดเรียบร้อยส่งไปที่บัญชี
   - บัญชีดำเนินการคืนเงิน
   - การเงินส่งเรื่องให้ธนาคารเพื่อคืนเงินแต่ละช่องทาง
   - การเงิน update status การคืนเงิน
   - ระบบส่ง SMS/E-mail ให้ผู้โดยสารเมื่อคืนเงินเรียบร้อย
   - voucher ระบบ generate voucher ส่งให้ผู้โดยสารพร้อม T&C

1. ในหน้า website B2C / B2B
   - ผู้โดยสาร Log in เพื่อ Manage Booking
   - สามารถ เลือก Option ได้ตามเงื่อนไข ข้อ 1.3

1. เจ้าหน้าที่สามารถดึง report ดูได้ว่า ผู้โดยสารในเที่ยวบิน Flight IRR มีการเลือก Option หรือยังไม่ได้เลือก
1. Staff  สามารถเปลี่ยน option ได้เมื่อเลือกไปแล้ว (หลังบ้าน)

