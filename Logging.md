# Daglig logg
## 05.02.25 - Onsdag:
- Gikk gjennom informasjon om prøvefagprøven.
- Skrevet planleggingen.
- Tegnet skisser med DrawSQL (datamodell) og Figma (apper).
- Gjort noen endringer i planlegging for å tilpasse datamodellen og appene (det endte opp annerledes enn forventet).
- Notert ned Views, Prosedyrer og Triggere som kreves i planen.
## 06.02.25 - Torsdag:
- Satt opp modul og rolle for å kunne jobbe på appene.
- Satt opp tabellene, views og prosedyren.
  - Jeg har jobbet med sikkerhet, inkludert triggere og views.
    - Det ble kaos her. Det begynte med OrgUnits, men jeg kom borti en stopp. Da lagde jeg en ekstra tabell for custom roller, men da ble det ikke "skikkelig". Da prøvde jeg å blande OrgUnits inni, men da ble det enda mer rot. Prøver å fikse i morgen.
  - AVVIK: Har laget et custom view for ReservationsHolders tabellen. Denne kreves for å få nødvendig informasjon mer direkte enn selve tabellen, som gjør ting mye lettere.
## 07.02.25 - Fredag:
- Fikset opp i sikkerheten ved hjelp av Capabilities. Gått gjennom alle triggere og views, og vurdert hvilke tilganger Admin og Kunde bør ha, og implementert.
- Lagt til to tabeller: Tables (bordene deres, inkludert antall seter) og ReservationsTables (for å linke en reservation til ett eller flere bord)
  - Dette er for å få med endringen som jeg fikk. Det var at det måtte være logikk for to firmannsbord og to tomannsbord.
- Begynt på appen. Har jobbet mye med kunden sin side, og "New Revision" modalen.
- Har jobbet med BookReservation prosedyren for å tilpasse endringen. Ble ikke helt ferdig
## (08-09).02.25 - Helg:
- 
## 10.02.25 - Mandag:
- 
## 11.02.25 - Tirsdag:
- 
