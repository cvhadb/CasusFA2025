```
┌─────────────────────────────────────────────────────────────────┐ 
│                    PLANNING TOOL SYSTEEM                         │ 
├─────────────────────────────────────────────────────────────────┤ 
│                                                                   │ 
│  ┌─────────┐                                                     │ 
│  │ Manager │                                                     │ 
│  └────┬────┘                                                     │ 
│       │                                                          │ 
│       ├──► UC01: Teams en werknemers beheren                    │ 
│       ├──► UC02: Taken toewijzen en beheren                     │ 
│       ├──► UC03: Verlof goedkeuren/afwijzen                     │ 
│       ├──► UC04: Centraal planningsbord gebruiken               │ 
│       ├──► UC05: Vestigingen beheren (CRUD)                     │ 
│       ├──► UC06: Taken beheren (CRUD)                           │ 
│       ├──► UC07: Werknemers beheren (CRUD)                      │ 
│       ├──► UC08: Dashboard met KPI's bekijken                   │ 
│       ├──► UC09: Plant details bekijken                         │ 
│       ├──► UC10: Notificaties bekijken                          │ 
│       ├──► UC11: Takenplanning per werknemer bekijken           │ 
│       ├──► UC12: Taken herplannen bij afwezigheid               │ 
│       └──► UC16: Taken overzicht bekijken        [TOEGEVOEGD]   │ 
│                                                                   │ 
│  ┌───────────┐                                                   │ 
│  │ Supervisor│                                                   │ 
│  └─────┬─────┘                                                   │ 
│        │                                                          │ 
│        ├──► UC09: Plant details bekijken                         │ 
│        ├──► UC08: Dashboard met KPI's bekijken                   │ 
│        ├──► UC13: Teamplanning bekijken                          │ 
│        ├──► UC14: Eigen planning bekijken                        │ 
│        ├──► UC15: Taken van team filteren/zoeken                │ 
│        ├──► UC10: Notificaties bekijken                          │ 
│        ├──► UC05: Vestigingen beheren (CRUD)                     │ 
│        ├──► UC06: Taken beheren (CRUD)                           │ 
│        ├──► UC07: Werknemers beheren (CRUD)                      │ 
│        └──► UC16: Taken overzicht bekijken       [TOEGEVOEGD]   │ 
│                                                                   │ 
│  ┌──────────┐                                                    │ 
│  │Werknemer │                                                    │ 
│  └────┬─────┘                                                    │ 
│       │                                                          │ 
│       ├──► UC14: Eigen planning bekijken                         │ 
│       ├──► UC16: Taken overzicht bekijken                        │ 
│       ├──► UC17: Taken filteren/zoeken (eigen)   [HERNOEMD]     │ 
│       ├──► UC18: Taak markeren als voltooid                      │ 
│       ├──► UC19: Afwezigheid melden (ziekte)                     │ 
│       ├──► UC20: Verlof aanvragen                                │ 
│       ├──► UC21: Afwezigheden opvolgen en beheren                │ 
│       ├──► UC10: Notificaties bekijken                           │ 
│       └──► UC22: Chatbot raadplegen over taken (extra)          │ 
│                                                                   │ 
│  ┌─────────┐                                                     │ 
│  │ Systeem │ (automatisch)                                       │ 
│  └────┬────┘                                                     │ 
│       │                                                          │ 
│       ├──► UC23: Taken auto-dealloceren bij afwezigheid         │ 
│       ├──► UC24: Notificatie versturen bij planningswijziging   │ 
│       ├──► UC25: Notificatie versturen bij ziekte               │ 
│       └──► UC26: KPI's automatisch berekenen                    │ 
│                                                                   │ 
└─────────────────────────────────────────────────────────────────┘ 
```

### `<<include>>` relaties:

#### **UC02: Taken toewijzen en beheren (Manager)**
- `<<include>>` **UC16: Taken overzicht bekijken (Manager)**

#### **UC04: Centraal planningsbord gebruiken (Manager)**
- `<<include>>` **UC16: Taken overzicht bekijken (Manager)**
- `<<include>>` **UC11: Takenplanning per werknemer bekijken (Manager)**

#### **UC12: Taken herplannen bij afwezigheid (Manager)**
- `<<include>>` **UC16: Taken overzicht bekijken (Manager)**

#### **UC13: Teamplanning bekijken (Supervisor)**
- `<<include>>` **UC16: Taken overzicht bekijken (Supervisor)**

#### **UC15: Taken van team filteren/zoeken (Supervisor)**
- `<<include>>` **UC16: Taken overzicht bekijken (Supervisor)**

#### **UC17: Taken filteren/zoeken eigen (Werknemer)**
- `<<include>>` **UC16: Taken overzicht bekijken (Werknemer)**

#### **UC21: Afwezigheden opvolgen (Werknemer)**
- `<<include>>` **UC19: Afwezigheid melden (Werknemer)**
- `<<include>>` **UC20: Verlof aanvragen (Werknemer)**


### `<<extends>>` relaties:

#### **UC22: Chatbot raadplegen (Werknemer)**
- `<<extends>>` **UC16: Taken overzicht bekijken (Werknemer)**


---

## Want:

✅ **Manager** moet de de taken (UC16) kunnen zien om ze toe te kennen (UC02)
✅ **Supervisor** moet de taken (UC16) kunnen zien om het team te leiden (UC13, UC15)  
✅ **Werknemer** moet zijn eigen taken (UC16) kunnen zien om ze te filteren (UC17)
✅ **Werknemer** moet afwezigheden opvolgen (UC21) om afwezigheid te melden (UC19) en verlof aan te vragen (UC20)
✅ **De Chatbot** (UC22) is een extra functionaliteit dat een werknemer toelaat taken overzicht te bekijken (UC16)
