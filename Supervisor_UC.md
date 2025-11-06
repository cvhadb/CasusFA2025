### UC13: Een supervisor kan de planning van zijn team en zijn eigen planning bekijken

**Primaire actor:** Supervisor

**Stakeholders:**
- Supervisor: wil teamoverzicht en eigen planning
- Teamleden: hun planning wordt gecontroleerd
- Manager: verwacht dat supervisor team monitort
- Organisatie: wil dat supervisors teams efficiënt begeleiden

**Precondities:**
- Supervisor is ingelogd en geauthenticeerd
- Supervisor is toegewezen aan minimaal één team
- Team heeft werknemers en eventueel toegewezen taken

**Postcondities:**
- Supervisor heeft actueel overzicht van teamplanning en eigen planning
- Geen data wordt gewijzigd (read-only functie)

**Normaal verloop:**
1. Supervisor wil planningsoverzicht bekijken
2. Systeem toont standaardweergave met eigen planning en team planning
3. Systeem toont supervisor's eigen toegewezen taken met status, deadline en prioriteit
4. Systeem toont planning van alle teamleden met hun taken
5. Supervisor selecteert een weergavemodus (dag, week, maand)
6. Systeem toont planning van de geselecteerde tijdsperiode
7. Systeem visualiseert:
   - Toegewezen taken per werknemer 
   - Capaciteitsbenutting per werknemer 
   - Deadlines en prioriteiten
   - Afwezigheden (verlof, ziekte)
8. Supervisor selecteert individuele taak voor detailweergave
9. Systeem toont taakdetails
10. Supervisor past filters toe (werknemer, status, vestiging, prioriteit)
11. Systeem toont gefilterde resultaten

**Alternatieve verlopen:**
- 7a. Een of meerdere werknemers hebben overcapaciteit (>90%):
  - Systeem markeert deze werknemers 
  - Supervisor ziet waarschuwingsindicator
  - Keer terug naar stap 7 normaal verloop
- 7b. Er zijn niet-toegewezen taken in het team:
  - Systeem toont sectie "Niet-toegewezen taken"
  - Keer terug naar stap 7 normaal verloop
- 3a. Supervisor heeft geen eigen taken:
  - Systeem toont boodschap "Geen taken momenteel toegewezen"
  - Keer terug naar stap 3 normaal verloop
- 10a. Supervisor wil de planning exporteren:
  - Systeem biedt export functie
  - Systeem genereert rapport met huidige weergave
  -  Keer terug naar stap 10 normaal verloop

**Domeinspecifieke regels:**

**DR_PLANNING_01**: Supervisor kan enkel planning zien van teams waaraan hij/zij is toegewezen.

**DR_PLANNING_02**: Historische planning is toegankelijk tot 3 maanden terug.

**DR_PLANNING_03**: Toekomstige planning is zichtbaar tot maximaal 6 maanden vooruit.

**DR_PLANNING_04**: Capaciteitsbenutting wordt berekend als: (som geschatte uren toegewezen taken / beschikbare uren) × 100%.

**Op te klaren punten:**
- Moet supervisor notificaties kunnen activeren voor specifieke events (bijv. overcapaciteit)?
- Kunnen supervisors commentaar toevoegen aan taken (read-only context)?
- Moet er real-time synchronisatie zijn of periodieke refresh?
- Kan supervisor aanbevelingen doen aan manager voor hertoewijzing?
