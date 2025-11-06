Use case UC20: Een werknemer kan een afwezigheid melden en zijn afwezigheden opvolgen en beheren

Primaire actor: Werknemer

Stakeholders:

· Manager (moet op de hoogte zijn van afwezigheden)

· Supervisor (moet op de hoogte zijn van afwezigheden in zijn team)

· Team: wordt beïnvloed door afwezigheid

· HR: moet afwezigheden bijhouden

Precondities:

· Werknemer is ingelogd en geauthenticeerd

· De werknemer heeft een actieve arbeidsrelatie en actief account

· Werknemer heeft mogelijk toegewezen taken

Postcondities:

· Het systeem heeft de afwezigheid geregistreerd

· Bij ziekte: het systeem stuurt onmiddellijke notificatie naar manager

· Bij verlof: aanvraag wacht op goedkeuring

· Toegewezen taken in afwezigheidsperiode krijgen status "niet toegewezen"

· Werknemer ziet afwezigheid in persoonlijk overzicht

Normaal verloop (afwezigheid melden):

1\. Werknemer wil een afwezigheid melden

2\. Systeem toont overzicht van geplande en historische afwezigheden

3\. Werknemer selecteert "nieuwe afwezigheid melden"

4\. Systeem vraagt type afwezigheid: ziekte of verlof

5\. Werknemer selecteert type afwezigheid

6\. Systeem toont formulier voor afwezigheidsdetails

7\. Werknemer vult in: startdatum, einddatum (indien gekend), reden (optioneel voor verlof)

8\. Systeem toont overzicht van taken die beïnvloed worden door deze afwezigheid

9\. Werknemer bevestigt de afwezigheidsmelding

10\. Systeem valideert de afwezigheid (DR\_AFW\_01, DR\_AFW\_02)

11\. Systeem registreert de afwezigheid

12\. Bij ziekte: Systeem voert auto-dealloceert taken en stuurt notificatie naar manager

13\. Bij verlof: Systeem creëert verlofaanvraag met status "in behandeling"

14\. Systeem toont bevestiging

15\. Systeem updatet beschikbaarheidsplanning

Systeem verwittiged notificatie naar manager

Alternatieve verlopen:

· 10a. Overlappende afwezigheid gedetecteerd:

o Systeem toont waarschuwing met bestaande afwezigheid

o Keer terug naar stap 7 van het normale verloop

· 2a. Werknemer wijzigt bestaande afwezigheid:

o Bij ziekte: werknemer kan einddatum bijwerken (verlengen/verkorten)

o Bij verlof: alleen mogelijk indien status = "in behandeling" of "goedgekeurd" met herbevestiging manager (systeem valideert naar dom regel)

o Systeem hervalideert beïnvloede taken

· 2b. Werknemer annuleert afwezigheid:

o Systeem vraagt bevestiging

o Bij verlof: mogelijk tot 24u voor startdatum

o Bij ziekte: alleen toekomstige afwezigheden

o Systeem herstelt taken NIET automatisch (manager moet hertoewijzen)

Domeinspecifieke regels:

· DR\_AFW\_01: Ziektemelding moet minimaal de startdatum en einddatum bevatten.

· DR\_AFW\_02: Verlofaanvraag moet minimaal 5 werkdagen op voorhand ingediend worden, tenzij uitzonderlijke omstandigheden.

· DR\_AFW\_03: Overlappende afwezigheidsperiodes voor dezelfde werknemer zijn niet toegestaan.

· DR\_AFW\_04: Bij afwezigheid worden alle taken in de afwezigheidsperiode automatisch gedealloceerd (status = "niet toegewezen").

· DR\_AFW\_05: Een afwezigheid kan enkel geannuleerd worden minimum 24 uur voor aanvang, behalve bij ziekte.

Op te klaren punten:

· Moet de werknemer documentatie kunnen uploaden (bijv. doktersattest)?

· Hoe lang blijven historische afwezigheden zichtbaar?

· Kunnen werknemers zien hoeveel verlofdagen ze nog hebben?

· Moet er een optie zijn voor deeltijdse afwezigheid (halve dagen)?

· Wat gebeurt er met taken die al gestart zijn bij ziektemelding?(misschien terug in de pool met priomelding?)


Use case UC14: Een werknemer kan zijn eigen planning bekijken

Primaire actor: Werknemer

Stakeholders:

· Manager: verwacht dat werknemer planning volgt

· Supervisor: verwacht dat werknemer planning volgt

· Team: wordt beïnvloed door werknemer's uitvoering

· Organisatie: wil dat werknemers hun prioriteiten kennen

Precondities:

· Werknemer is ingelogd en geauthenticeerd (vragen voor op infomement)

· De werknemer heeft een actief account(?? Vragen voor op infomoment)

· Er bestaat een planning voor de werknemer met mogelijk toegewezen taken

Postcondities:

· De werknemer heeft inzicht in zijn eigen planning

· De werknemer is op de hoogte van zijn toegewezen taken en werkuren

Normaal verloop:

1\. werknemer wil eigen planning bekijken

2\. Het systeem toont het overzicht van huidige en toekomstige taken

3\. De werknemer maakt selectie

4\. Het systeem toont overzicht van de dagplanning, werkbelasting, dringende taken en aankomende taken

5\. De werknemer selecteert een specifieke taak

6\. Het systeem toont een beschrijving, status, prioriteit, duur, deadline, locatie, naam/namen toegewezen team, eventuele bijlagen en taakgeschiedenis (details)

7\. De werknemer navigeert naar takenoverzicht op maandbasis

8\. Het systeem past de weergave aan op basis van de geselecteerde periode

9\. De werknemer keert terug naar het overzicht

Alternatieve verlopen:

· 2a. Werknemer heeft geen toegewezen taken:

o Systeem toont boodschap "Geen taken momenteel toegewezen"

o Systeem suggereert contact met supervisor

· 2b. Werknemer heeft overcapaciteit (>100%):

o Systeem toont waarschuwingsbericht

o Systeem suggereert contact met manager/supervisor

· 5a. Werknemer filtert taken:

o Systeem biedt filters: status, prioriteit, vestiging, deadline

o Systeem toont gefilterde resultaten

Domeinspecifieke regels:

· DR\_PLANNING\_05: Werknemer kan enkel eigen toegewezen taken zien, niet die van collega's.

· DR\_PLANNING\_06: Taken met deadline binnen 48 uur worden visueel gemarkeerd als urgent.

· DR\_PLANNING\_07: Voltooide taken blijven zichtbaar in de planning gedurende 30 dagen.

· DR\_PLANNING\_08: Werknemer ziet alleen taken toegewezen vanaf vandaag tot 3 maanden vooruit.

Op te klaren punten:

· Moet de werknemer kunnen zien wie de taak heeft toegewezen

· Kunnen werknemers notities/commentaar zien die aan taken gekoppeld zijn?(ja

· Moet er synchronisatie zijn met externe kalenders (Google Calendar, Outlook)

· Kunnen werknemers de volgorde van taken aanpassen (prioriteit suggereren)?

· Moet de planning print/exporteerbaar zijn?

· Is er nood aan archief op klantenniveau



Use case UC24: manager past planning aan

Primaire actor: manager

Stakeholders:

· Werknemer: wil tijdig op de hoogte zijn van planningswijzigingen

· Manager: moet weten wanneer werknemers afwezig zijn

· Organisatie: wil effectieve communicatie en snelle reactie

Precondities:

· Notificatiesysteem is actief

· Gebruikers hebben notificatievoorkeuren ingesteld

· Er vindt een trigger event plaats (taakwijziging, afwezigheid)

Postcondities:

· Betrokken gebruikers ontvangen notificatie

· Notificatie is gelogd in het systeem

· Gebruikers kunnen notificatie bekijken en actie ondernemen

Normaal verloop : Planningswijziging voor werknemer

1\. Systeem detecteert planningswijziging (nieuwe taak, taakwijziging, deallocatie)

2\. Systeem identificeert betrokken werknemer(s)

3\. Systeem controleert notificatievoorkeuren van werknemer

4\. Systeem creëert notificatiebericht met:

a. Type wijziging (nieuwe taak, gewijzigde taak, verwijderde taak)

b. Taakdetails (naam, deadline, prioriteit)

c. Wie de wijziging heeft aangebracht

d. Tijdstip van wijziging

5\. Systeem verstuurt notificatie via geactiveerde kanalen (in-app, email, push)

6\. Systeem markeert notificatie als "ongelezen" voor werknemer

7\. Systeem logt notificatie met timestamp

8\. Werknemer ontvangt notificatie

9\. Werknemer opent applicatie en ziet notificatie in notificatiepaneel

10\. Werknemer klikt op notificatie

11\. Systeem navigeert naar relevante taak/planning

12\. Systeem markeert notificatie als "gelezen"

Normaal verloop: Afwezigheidsmelding voor manager

1\. Systeem detecteert afwezigheidsmelding (ziekte of goedgekeurd verlof)

2\. Systeem identificeert manager van de afwezige werknemer

3\. Systeem voert UC23 uit (taken auto-dealloceren)

4\. Systeem creëert notificatiebericht voor manager met:

a. Type afwezigheid (ziekte, verlof)

b. Werknemer naam

c. Startdatum en einddatum (indien bekend)

d. Lijst van gedealloceerde taken

e. Urgentie indicator (indien taken met hoge prioriteit betrokken zijn)

5\. Systeem verstuurt notificatie via geactiveerde kanalen

6\. Systeem markeert notificatie als "urgent" indien taken met deadline < 3 dagen betrokken zijn

7\. Systeem logt notificatie

8\. Manager ontvangt notificatie

9\. Manager opent applicatie

10\. Manager klikt op notificatie

11\. Systeem navigeert naar planningsbord met gedealloceerde taken gemarkeerd

12\. Manager kan direct herplanning starten (UC04, UC12)

Alternatieve verlopen:

· 3a. Werknemer heeft notificaties uitgeschakeld:

o Systeem slaat notificatie op in notificatiepaneel

o Systeem verstuurt geen externe notificatie

o Werknemer ziet notificatie bij volgende login

· 5a. Email delivery faalt:

o Systeem probeert opnieuw (max 3 pogingen)

o Systeem logt error

o In-app notificatie blijft beschikbaar

· 6a. Urgente notificatie (deadline < 24u):

o Systeem markeert notificatie als "urgent" met visuele indicator

o Systeem verstuurt push notificatie ongeacht voorkeuren

Domeinspecifieke regels:

DR\_NOTIFICATION\_01: Notificaties worden binnen 30 seconden na trigger event verstuurd.

DR\_NOTIFICATION\_02: Urgente notificaties (afwezigheid, deadline <24u) worden altijd verstuurd, ongeacht gebruikersvoorkeuren.

DR\_NOTIFICATION\_03: Notificaties blijven 90 dagen bewaard in het systeem.

DR\_NOTIFICATION\_04: Gebruikers kunnen notificatievoorkeuren instellen per type event (taak, afwezigheid, deadlines).

DR\_NOTIFICATION\_05: Bij afwezigheid wordt enkel de directe manager genotificeerd, niet het volledige team.

DR\_NOTIFICATION\_06: Gegroepeerde notificaties worden verstuurd bij >5 individuele events binnen 1 uur.

Op te klaren punten:

· Moeten werknemers real-time push notificaties ontvangen of batch (einde dag)?

· Kunnen gebruikers notificatiekanalen per event type configureren?

· Moet er een escalatiemechanisme zijn indien manager niet reageert op urgente afwezigheid?

· Kunnen gebruikers notificaties snoozen/uitstellen?

· Moet er een dashboard zijn met notificatiestatistieken?

· Worden teamleden ook genotificeerd bij collega-afwezigheid?
