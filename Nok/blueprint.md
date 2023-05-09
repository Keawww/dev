# Blueprint

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


# Universe



## <font color='dodgerblue'>Infra Layer</font>

### AirFase
```mermaid
graph

subgraph AirFase
    subgraph AIRFASESV
       af([X4.24.246])
    end
    subgraph WGCM
       wgcm([X3.40.33])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class AirFase system
class AIRFASESV,WGCM server
```


### Corp Web
```mermaid
graph

subgraph Corp-Web
    direction RL
    subgraph WEBAPP01
       wp1([X3.40.13])
    end
    
    subgraph WEBAPP02
       wp2([X3.40.14])
    end
    
    subgraph WEBAPI01
       wa1([X3.40.31])
    end
    
    subgraph WEBAPI02
       wa2([X3.40.32])
    end
    
    subgraph WEBDEV
       wdev([X4.23.21])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class Corp-Web system
class WEBAPP01,WEBAPP02,WEBAPI01,WEBAPI02,WEBDEV server
```


### Domain Controller
```mermaid
graph

subgraph Domain-Controller
    subgraph NOKDC1
        ndc1([X4.24.200])
    end
    subgraph NOKDC2
        ndc2([X4.24.101])
    end
    subgraph DC01
        dc1([X4.24.102])
    end
    subgraph DC02
        dc2([X4.24.201])
    end
    subgraph NOKADCN01
        nad1([X4.24.202])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray
classDef check color: red, fill: gold, stroke: red

class Domain-Controller system
class NOKDC1,NOKDC2,DC01,DC02,NOKADCN01 server
```


### File Sharing
```mermaid
graph

subgraph File-Sharing
    subgraph ALTIRISDB
        atrdb([X4.24.213])
    end
    
    subgraph HQ-FS
        hqfs([X2.1.54])
    end
    
    subgraph NETBACKUP01
        nb1([X4.24.107])
    end
    
    subgraph NETBACKUP02
        nb2([X4.24.108])
    end
    
    subgraph NETBACKUP03
        nb3([X2.1.53])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class File-Sharing system
class ALTIRISDB,HQ-FS,NETBACKUP01,NETBACKUP02,NETBACKUP03 server
```


### HRIS
```mermaid
graph

subgraph HRIS
    subgraph HRIS01
        hris1([X4.24.61])
    end
    
    subgraph HRIS02
        hris2([X4.24.62])
    end
    
    subgraph HRISDB
        hrisdb([X4.24.65])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class HRIS system
class HRIS01,HRIS02,HRISDB server
```






### Nok CRM
```mermaid
graph

subgraph NokCRM
    subgraph CRMAPP01
        crma1([X4.23.91])
    end
    
    subgraph CRMAPP02
        crma2([X4.23.92])
    end
    
    subgraph CRMDB01
        crmd1([X4.23.93])
    end
    
    subgraph CRMDB02
        crmd2([X4.23.94])
    end
    
    
    crma1 -.- crmd1
    crma2 -.- crmd2
    
classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class NokCRM system
class CRMAPP01,CRMAPP02,CRMDB01,CRMDB02 server
end
```


### Nok DD
```mermaid
graph

subgraph NokDD
    subgraph Cluster
        subgraph NOKDDFE01
            ndd1([X4.23.121])
        end
    
        subgraph NOKDDFE02
            ndd2([X4.23.122])
        end
        
        ncl[VIP<br>X4.23.xx]
    end
    
    ncl -.- nsql1
    
    subgraph NDDSQL01
        nsql1([X4.23.123])
    end
    
    subgraph NDDSQL02
        nsql2([X4.23.124])
    end
    
    subgraph NOKDDTEST_2008R2
        nddt([X2.1.48])
    end
    
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class NokDD system
class NOKDDFE01,NOKDDFE02,NDDSQL01,NDDSQL02,NOKDDTEST_2008R2 server
```


### Nok Fanclub
```mermaid
graph

subgraph Nok-FanClub
    subgraph VIP
        vip([X4.23.88])
    end
    subgraph NOKFANCLUB01
        nfc1([X3.40.19])
    end
    subgraph NOKFANCLUB02
        nfc2([X3.40.20])
    end
    
    vip -.- nfc1
    vip -.- nfc2
    
    subgraph WEBSQL01
        wsql1([X4.23.81])
    end
    subgraph WEBSQL02
        wsql2([X4.23.82])
    end
    subgraph WEBDB01
        wdb1([X4.23.165])
    end
    subgraph WEBDBA
        wdba([X4.23.161])
    end
    subgraph LOADBALANCER02
        lb2([X4.24.132])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray
classDef check color: red, fill: gold, stroke: red

class Nok-FanClub system
class NOKFANCLUB01,NOKFANCLUB02,WEBSQL01,WEBSQL02,WEBDB01,WEBDBA,LOADBALANCER02 server

class VIP,LOADBALANCER02 check

```


### Nok POS
```mermaid
graph

subgraph Nok-POS
    subgraph NOKPOS1
        np1([X4.24.221])
    end
    
    subgraph NOKPOS2
        direction TB
        np2([X4.24.222])
        np21([X4.24.226<br>POSCluster])
        np22([X4.24.225<br>PostOffice])
        np23([X4.24.226<br>PostDB])
    end
    
    subgraph POSDBTEST
        pdbt([X4.24.26])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class Nok-POS system
class NOKPOS1,NOKPOS2,POSDBTEST server

```


### NokSmart
```mermaid
graph

subgraph NokSmart
    subgraph NOKSMART01
       nsm1([X4.23.51])
    end
    
    subgraph NOKSMART02
       nsm2([X4.23.52])
    end
    
    subgraph SMARTREPORT
       nsr([X4.23.53])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class NokSmart system
class NOKSMART01,NOKSMART02,SMARTREPORT server
```


### IT UR
```mermaid
graph

subgraph IT-UR
    subgraph NOKREQUEST
        nr([X4.24.243])
    end
    
    subgraph SHAREPOINTDB01
        spdb1([X4.24.116])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class IT-UR system
class NOKREQUEST,SHAREPOINTDB01 server
```

### iWork/iDoc
```mermaid
graph

subgraph iWork
    subgraph IWORK2
        iw2([X4.24.117])
    end
    
    subgraph SHAREPOINTDB
        spdb([X4.24.115])
    end
    
    subgraph NOKSHAREPOINT02
        nsp2([X4.24.112])
    end
    
    subgraph NOKPURCHASE01
        npc1([X4.23.24])
    end
    
    subgraph ARC_APPLOG
        aal([X2.1.77])
    end
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class iWork system
class IWORK2,SHAREPOINTDB,NOKSHAREPOINT02,NOKPURCHASE01,ARC_APPLOG server
```


### Navision
```mermaid
graph

subgraph Navision
   subgraph Navision01
       nv1([X4.24.198])
   end
   
   subgraph Navision02
       nv2([X4.24.199])
   end
   
   subgraph NAV-STAGING
       nv3([X4.24.206])
   end
   
   subgraph NAVISIONAPPTEST
       nvt([X4.1.56])
   end
   
   subgraph NAVISIONDB
       nvdb([X4.24.195])
   end
   
   nv1 --- nvdb
   nv2 --- nvdb
   
end
   
classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray

class Navision system
class Navision01,Navision02,NAV-STAGING,NAVISIONAPPTEST,NAVISIONDB server
   
```






## <font color='dodgerblue'>Application Layer</font>

### <font color='darkorange'>Corp Web</font>
```mermaid
graph

subgraph CMS
    subgraph NOKFANCLUB01
    end
    
    subgraph NOKFANCLUB02
    end
end

subgraph Radixx
    ez([Ezy])
    go([Go])
    res([Res])
    resdb([Connect<br>Point])
end

subgraph OTA
    subgraph API4
       otas(OTA)
    end
end

subgraph Payment
    subgraph API3
       pay([Payment])
    end
    
    subgraph NOKGATEWAY
       ngw([Payment])
       ngwqr([QR]) 
       ngwatm([ATM]) 
       ngwcs([CS]) 
    end
end

subgraph Corp-Web
    subgraph WebDBA
       wdba[(WebDBA)] 
    end
    
    subgraph WebApp02
    end
    
    subgraph NOKCACHE
        direction TB
        rd1([REDIS1-REMOVE])
        rd2([REDIS2-REMOVE])
    end
    
    subgraph WebApp01
       bk([Booking]) 
       nfc([NFC]) 
       ck([On-line<br>Checkin]) 
       pm([Payment]) 
       ag([Agent<br>Portal]) 
       et([E-Tax]) 
       cms([CMS]) 
    end
    
    bk -.- ez
    resdb -.- |Pax Info| et
    ck -.- go
    cms -.- NOKFANCLUB01
    
end

classDef system color: gray, stroke: gray, stroke-dasharray: 6 6
classDef server color: gray, fill: gold, stroke: gray
classDef check color: red, fill: gold, stroke: red

class Corp-Web system
class WebApp01,WebApp02,WebDBA,NOKFANCLUB01,NOKFANCLUB02 server

class Radixx system
class CMS system

class Payment system
class API3 server

class NOKGATEWAY system
class NOKGATEWAY server

class OTA system
class API4 server

class NOKCACHE,rd1,rd2 check
```


