## Niet-Functionele Requirements (NFR's)

### NFR 1: Gebruiksvriendelijkheid - Leercurve

**Categorie NFR:** Usability - Learnability (ISO 25010)

**Indicator:** Tijd die een nieuwe gebruiker nodig heeft om basistaken uit te voeren zonder hulp

**Meetvoorschrift:**
- Selecteer 10 representatieve gebruikers (3 managers, 3 supervisors, 4 werknemers) zonder voorafgaande kennis van het systeem
- Geef korte introductiepresentatie van 15 minuten over hoofdfunctionaliteiten
- Laat gebruikers 5 typische taken uitvoeren zonder hulp:
  1. Inloggen en eigen dashboard bekijken
  2. Eigen planning raadplegen (werknemer/supervisor)
  3. Taak markeren als voltooid (werknemer)
  4. Afwezigheid melden (werknemer)
  5. Taak toewijzen aan werknemer (manager/supervisor)
- Meet de tijd vanaf start opdracht tot succesvolle afronding
- Registreer aantal fouten/misstappen per taak
- Bereken gemiddelde voltooiingstijd en foutpercentage

**Norm:** 
- Minimaal 80% van de nieuwe gebruikers moet alle 5 basistaken succesvol uitvoeren binnen 30 minuten na de introductiepresentatie
- Maximaal 2 fouten per taak gemiddeld
- Succespercentage (taak correct afgerond) moet >90% zijn

---

### NFR 2: Performance - Responstijd

**Categorie NFR:** Performance Efficiency - Time Behaviour (ISO 25010)

**Indicator:** Responstijd van het systeem bij gebruikersinteracties

**Meetvoorschrift:**
- Meet de responstijd voor kritieke gebruikersacties gedurende testperiode van 5 werkdagen
- Test onder realistische load: 100 gelijktijdige gebruikers
- Kritieke acties om te meten:
  1. Laden van planningsbord met 50 werknemers en 200 taken
  2. Toewijzen van taak aan werknemer (drag-and-drop)
  3. Opslaan van nieuwe afwezigheid
  4. Laden van dashboard met KPI's en grafieken
  5. Zoeken/filteren van taken (resultaatset van 100 taken)
- Meet tijd tussen gebruikersactie en volledige weergave resultaat
- Registreer 95e percentiel responstijd voor elke actie
- Test op verschillende tijdstippen (piekuren vs. rustige uren)

**Norm:**
- 95% van alle acties moet responstijd hebben van <2 seconden
- Planningsbord laden: <3 seconden
- Dashboard laden met grafieken: <4 seconden
- Drag-and-drop taaktoewijzing: <1 seconde (visuele feedback onmiddellijk, opslaan asynchroon)
- Zoeken/filteren: <1,5 seconde
- Geen enkele actie mag >10 seconden duren

---

### NFR 3: Betrouwbaarheid - Databehoud

**Categorie NFR:** Reliability - Fault Tolerance (ISO 25010)

**Indicator:** Percentage gegevensverlies bij systeemfalen of onverwachte gebeurtenissen

**Meetvoorschrift:**
- Simuleer verschillende failure scenarios gedurende testperiode:
  1. Onverwacht afsluiten van browser tijdens taaktoewijzing (10x)
  2. Netwerk-onderbreking tijdens opslaan van planning (10x)
  3. Gelijktijdige wijziging van dezelfde taak door 2 managers (conflict test, 10x)
  4. Server restart tijdens actieve gebruikerssessies (5x)
  5. Database verbinding verlies tijdens transactie (10x)
- Voor elk scenario:
  - Voer actie uit tot 50% voortgang
  - Introduceer failure
  - Herstel systeem
  - Controleer of gegevens correct opgeslagen/hersteld zijn
- Bereken percentage scenarios waarbij:
  - Geen gegevensverlies optrad (correct opgeslagen of volledig teruggezet)
  - Gedeeltelijk gegevensverlies (incomplete data)
  - Volledig gegevensverlies
- Test ook auto-save functionaliteit: wijziging moet binnen X seconden bewaard worden

**Norm:**
- 99% van transacties moet correct afgehandeld worden (geen gegevensverlies of volledige rollback)
- Bij falen tijdens transactie: systeem moet automatisch rollback uitvoeren
- Auto-save functionaliteit moet wijzigingen binnen 5 seconden bewaren
- Gelijktijdige wijzigingen: systeem moet conflict detecteren en gebruiker waarschuwen
- Na systeemfalen moet gebruiker kunnen doorgaan zonder gegevensverlies binnen 2 minuten na herstel

---

### NFR 4: Bruikbaarheid - Efficiëntie van gebruik

**Categorie NFR:** Usability - Operability (ISO 25010)

**Indicator:** Aantal klikken/acties nodig om veelgebruikte taken uit te voeren

**Meetvoorschrift:**
- Identificeer 8 meest uitgevoerde taken op basis van use cases:
  1. Taak toewijzen aan werknemer 
  2. Eigen planning raadplegen als werknemer
  3. Taak markeren als voltooid
  4. Afwezigheid (ziekte) melden
  5. Verlof aanvragen
  6. Dashboard met KPI's bekijken
  7. Notificaties bekijken en openen
  8. Werknemer toevoegen aan team
- Voor elke taak:
  - Tel aantal klikken/interacties vanaf homepage tot succesvolle afronding
  - Tel aantal schermovergangen
  - Meet tijd tot voltooiing door ervaren gebruiker
- Voer uit met 5 ervaren gebruikers per rol (manager, supervisor, werknemer)
- Bereken gemiddelde voor elke taak

**Norm:**
- Geen enkele veelgebruikte taak mag meer dan 5 klikken vereisen
- Specifieke normen per taak:
  - Taak toewijzen (drag-and-drop): 2 acties (selecteer + drop)
  - Eigen planning bekijken: 1 klik
  - Taak markeren als voltooid: 2 klikken
  - Ziekte melden: 3 klikken (navigeer > selecteer type > bevestig)
  - Dashboard bekijken: 1 klik
  - Notificatie openen: 1 klik
- Gemiddelde voltooiingstijd voor ervaren gebruiker per taak: <15 seconden (exclusief denktijd)
- Minimaal 90% van functionaliteiten toegankelijk binnen 2 klikken vanaf homepage

---

### NFR 5: Onderhoudbaarheid - Aanpasbaarheid

**Categorie NFR:** Maintainability - Modifiability (ISO 25010)

**Indicator:** Tijd en effort nodig om wijzigingen door te voeren in het systeem

**Meetvoorschrift:**
- Definieer 5 representatieve wijzigingsscenario's van verschillende complexiteit:
  1. **Klein**: Toevoegen van nieuw veld aan taakformulier (bijv. "Locatie notitie")
  2. **Klein**: Wijzigen van kleurcode voor capaciteitsvisualisatie
  3. **Gemiddeld**: Toevoegen van nieuwe notificatietype (bijv. "taak bijna verlopen")
  4. **Gemiddeld**: Aanpassen van autorisatielogica (nieuwe rol toevoegen)
  5. **Groot**: Toevoegen van nieuwe KPI in dashboard (inclusief backend berekening en visualisatie)
- Voor elk scenario:
  - Laat ontwikkelaar wijziging doorvoeren (zonder voorkennis van specifieke code)
  - Meet tijd vanaf start analyse tot deployment in test-omgeving
  - Tel aantal bestanden dat gewijzigd moet worden
  - Tel aantal regressiefouten na wijziging (via geautomatiseerde tests)
- Bereken gemiddelde effort per complexiteitscategorie
- Herhaal met 3 verschillende ontwikkelaars voor betrouwbaarheid

**Norm:**
- Kleine wijzigingen: <4 uur ontwikkeltijd, max 3 bestanden aangepast
- Gemiddelde wijzigingen: <2 werkdagen, max 8 bestanden aangepast
- Grote wijzigingen: <5 werkdagen, max 15 bestanden aangepast
- Code coverage van geautomatiseerde tests: >75%
- Regressiefouten na wijziging: 0 (alle tests moeten slagen)
- Modulaire architectuur: elke component moet onafhankelijk aanpasbaar zijn
- Documentatie: elke component moet gedocumenteerde interfaces hebben
- Gemiddelde tijd voor nieuwe ontwikkelaar om productief te worden: <3 werkdagen
