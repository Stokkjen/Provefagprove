# Systemdokumentasjon

## Oppgave
Oppgaven er å lage et system for en restaurant (og kundene deres), hvor restauranten kan se alle reservasjoner, og kundene skal kunne lage reservasjoner, se dem, og kunne kansellere dem.

## Universell Utforming
Jeg har brukt grids som er greie til å navigere i for de fleste, men det kan være litt slit å holde på å trykke på en liten rute for noen. Da har jeg prøvd å få til slik at det blir brukt modaler og knapper der mulig for lettere interaksjon. I tillegg vil dette gjøre det lettere å forstå hvordan en navigerer og gjør ting.

## Sikkerhet !
Her har jeg brukt noe som vi kaller Capabilities. Jeg har to capabilities: IsAdmin og IsCustomer. (Forklar hvordan de er tilgitt.) I SQL er det innebygde views som tillatter deg lett å sjekke hvilke capabilities noen har tilgang til. Jeg har da laget et view som er spesifisert mot dette systemet, som rett og slett returnerer om du har IsAdmin eller IsCustomer capabilitien, som gjør sikkerheten meget lett å håndtere.
I sikkerhets viewet til tabellene sjekker jeg om du har tilgang til tabellen (via et annet innebygd view som returnerer alle tabeller du har tilgang til via modulene nevnt tidligere), og jeg sjekker også opp mot om du har IsAdmin eller IsCustomer capabilities. Der blir det også litt mer custom basert på tabell. For eksempel: Admin skal ha tilgang til alle reservasjonene, men Customer skal bare ha tilgang til sine egne reservasjoner; men, hvis vi tenker på for eksempel åpningstider, da skal både Admin og Customer kunne se alt.
Vi bruker også mye triggere, som kjører sikkerhetssjekk omtrent likt som sikkerhets viewet til tabellene. Disse triggerene er da sjekker og logikk som kjører etter INSERT, UPDATE eller DELETE av data i spesifikke tabeller. Da må jeg, likt som i sikkerhets viewet til tabellene, legge til en sjekk på om du har tilgang til tabellen, men i tillegg til det, må jeg sjekke om de har Edit eller Delete permissions, kommer ann på hvilken trigger. I tillegg til det, likt som sikkerhets viewet til tabellene, må jeg sjekke opp om de er Admin eller Customer, og bruke logikk på hva Admin skal kunne gjøre og hva Customer skal kunne gjøre.

## Arkitektur !
### Frontend
- New Reservation:
  - Dette er egentlig en egen app, men blir brukt som en komponent jeg bruker i hovedappene.
  - Her kan du lage en reservasjon opptil to uker i fremtiden. Informasjon du gir er:
    - Gjester
    - Navn og Telefon (Bare hvis du er Admin; hvis du er Customer fylles disse automatisk inn)
    - Tid (Per nå er det slik at alle reservasjoner varer 2 timer, så en trenger bare å fylle inn starttid)
    - Kommentar (Dette kan da være hva som helst, for eksempel allergi)
- Admin:
  - New Reservation modalen er tilgjengelig, og åpnes av en knapp.
  - Admin har tilgang til fire forskjellige grids:
    - Today's Reservations: Viser alle reservasjoner hos restauranten som er i dag, som er kjekt for å ha god oversikt over dagen.
    - All Reservations: Viser alle reservasjoner som finnes. Her kan du også kansellere reservasjoner.
    - Reservations Holders: Her har de tilgang til alle som har laget en reservasjon. Du kan gjemme noen hvis de er urelevante, eller, for personvern, kan du anonymisere kunder, slik at informasjon som navn og telefon nummer fjernes.
    - Tables: Her har de tilgang til bordene deres. Her kan en ha en oversikt over bord en har.
- Customer:
  - New Reservation modalen er tilgjengelig, og åpnes av en knapp.
  - Her har kunden bare tilgang til sine egne reservasjoner.
  - Kunden kan kansellere en reservasjon om de vil.
### Backend (SQL)
- Tabeller
  - Reservations:
  - ReservationsHolders:
  - Tables:
  - ReservationsTables:
  - Uptimes: 
- Views
  - AllReservations:
  - 
- Prosedyrer
  - BookReservation:
  - 

## Teknologi
### Omega365 CTP (Core Technology Platform) rammeverk
- Dette er en av bedriftens standarder, og det er noe jeg har mye erfaring med.
- Det er veldig grei å bruke, fordi det finnes mange ferdig-lagte komponenter, som for eksempel grids som jeg brukte mye av.
- Dette rammeverket består da av:
  - Vue.js
  - Bootstrap
  - SQL
### Figma
- Dette er et fint værktøy for å tegne opp en skisse av en eller flere apper.
### DrawSQL
- Dette er flott for å ha en fin oversikt over en datamodell.
### Github
- Dette er et veldig greit verktøy for å dokumentere ting på, og er lett å dele.
- Det er ryddig og ser fint ut, og det er lett å få inn bilder og lignende for å illustrere.
