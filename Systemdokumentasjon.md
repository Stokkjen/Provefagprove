# Systemdokumentasjon

## Oppgave
Oppgaven er å lage et system for en restaurant (og kundene deres), hvor restauranten kan se alle reservasjoner, og kundene skal kunne lage reservasjoner, se dem, og kunne kansellere dem.

## Universell Utforming
Jeg har brukt grids som er greie til å navigere i for de fleste, men for noen kan det være litt slit å holde på å trykke på en liten rute. Da har jeg prøvd å få til slik at det blir brukt modaler og knapper der mulig for lettere interaksjon. I tillegg vil dette gjøre det lettere å forstå hvordan en navigerer og gjør ting.

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

## Sikkerhet
### Capabilities
Her har jeg brukt noe som vi kaller Capabilities. Jeg har to capabilities: "Can Administrate Omega Gourmet" (IsAdmin) og "Can Manage Reservations Omega Gourmet" (IsCustomer). Disse kan du da legge til på en eller flere roller.
### Moduler
Moduler har tilganger på tabeller og apper. Da har jeg laget to moduler: "Omega Gourmet Admin" og "Omega Gourmet Customer", slik at Admin har tilgang til Admin appen, mens Customer har tilgang til Customer appen. Som nevnt så kan du også gi tilgang til tabeller (Read, Edit og Delete). Da har jeg gitt Admin tilganger til omtrent alt, mens Customer får ikke like mange tilganger.
### Roller
Disse rollene er det som knytter Capabilities og Moduler til ett. Jeg har da to roller: "Omega Gourmet Admin" og "Omega Gourmet Customer" (lik Modulene). Så da har Admin rollen tilgang til Admin modulen og Admin capabilitien, og Customer rollen har tilgang til Customer modulen og Customer capabilitien. Disse knytter en da på noe som heter Org Units, og en person.
### Org Units
Dette er ikke veldig viktig for denne oppgaven, men simpelt forklart er dette en slags "lokasjon". Ved hjelpen av disse kan du da knytte roller til en person på en av disse lokasjonene.
### Custom view for tilganger
I SQL er det innebygde views som tillatter deg lett å sjekke hvilke capabilities noen har tilgang til. Jeg har da laget et view som er spesifisert mot dette systemet, som rett og slett returnerer om du har IsAdmin eller IsCustomer capabilitien, som gjør sikkerheten meget lett å håndtere.
### Sikkerhets view til tabeller
Her sjekker jeg om du har tilgang til tabellen (via et annet innebygd view som returnerer alle tabeller du har tilgang til via modulene nevnt tidligere), og jeg sjekker også opp mot om du har IsAdmin eller IsCustomer capabilities. Der blir det også litt mer custom basert på tabell. For eksempel: Admin skal ha tilgang til alle reservasjonene, men Customer skal bare ha tilgang til sine egne reservasjoner; men, hvis vi tenker på for eksempel åpningstider, da skal både Admin og Customer kunne se alt.
### Triggere
Triggere kjører sikkerhetssjekk omtrent likt som sikkerhets viewet til tabellene. Disse triggerene er da sjekker og logikk som kjører etter INSERT, UPDATE eller DELETE av data i spesifikke tabeller. Da må jeg, likt som i sikkerhets viewet til tabellene, legge til en sjekk på om du har tilgang til tabellen, men i tillegg til det, må jeg sjekke om de har Edit eller Delete permissions, kommer ann på hvilken trigger. I tillegg til det, likt som sikkerhets viewet til tabellene, må jeg sjekke opp om de er Admin eller Customer, og bruke logikk på hva Admin skal kunne gjøre og hva Customer skal kunne gjøre.

## Arkitektur
### Frontend
- New Reservation
  - Dette er egentlig en egen app, men blir brukt som en komponent jeg bruker i hovedappene.
  - Her kan du lage en reservasjon opptil to uker i fremtiden. Informasjon du gir er:
    - Gjester
    - Navn og Telefon (Bare hvis du er Admin; hvis du er Customer fylles disse automatisk inn)
    - Tid (Per nå er det slik at alle reservasjoner varer 2 timer, så en trenger bare å fylle inn starttid)
    - Kommentar (Dette kan da være hva som helst, for eksempel allergi)
- Admin
  - New Reservation modalen er tilgjengelig, og åpnes av en knapp.
  - Admin har tilgang til fire forskjellige grids:
    - Today's Reservations: Viser alle reservasjoner hos restauranten som er i dag, som er kjekt for å ha god oversikt over dagen.
    - All Reservations: Viser alle reservasjoner som finnes. Her kan du også kansellere reservasjoner.
    - Reservations Holders: Her har de tilgang til alle som har laget en reservasjon. Du kan gjemme noen hvis de er urelevante, eller, for personvern, kan du anonymisere kunder, slik at informasjon som navn og telefon nummer fjernes.
    - Tables: Her har de en oversikt over bordene deres.
- Customer
  - New Reservation modalen er tilgjengelig, og åpnes av en knapp.
  - Her har kunden bare tilgang til sine egne reservasjoner.
  - Kunden kan kansellere en reservasjon om de vil.
### Backend (SQL)
- Tabeller
  - Reservations: Her ligger mesteparten av informasjonen til reservasjonene, inkludert gjester, reservasjons holder, tid og om den er kansellert.
  - ReservationsHolders: Dette inneholder basic informasjon om forskjellige folk som har reservert. Hvis Admin la til personen, er det bare Navn og Telefon. Men hvis det er en Customer som har gjort en reservasjon, så vil den referere til kunden sin bruker i systemet.
  - Tables: Her har vi informasjon om bord som de har, og hvor mange seter hvert bord har.
  - ReservationsTables: Her kobler vi en reservasjon og et bord. Denne strukturen tillater en reservasjon å ha flere bord.
  - Uptimes: Her har vi oppetidene til restauranten.
- Views
  - AllReservations: Denne henter informasjon fra Reservations og ReservationsHolders tabellen for å få oversiktlig informasjon over alle reservasjoner. (Grunnet sikkerhets viewet i Reservations vil bare Customer se sine egne reservasjoner.)
  - ReservationsHolders: Grunnet valget i tabellen ReservationsHolders av enten direkte informasjon (navn og telefon) eller referanse til personen i systemet, tar dette viewet og kombinerer dem, slik at all informasjonen ligger på samme sted.
  - MyAccess: Dette viewet sjekker på Capabilities som du har, og returnerer IsAdmin og IsCustomer, som gjør ting mye lettere for sikkerheten i sikkerhets view til tabeller og triggere.
- Prosedyrer
  - BookReservation: Dette er en relativt avansert prosedyre. Denne booker en reservasjon for kunden. Her må den gjøre en god del sjekker og kalkulasjoner for å få ønsket resultat, som hovedsaklig er sjekk om det er nok bord for reservasjonen, og så kalkulere hvilke bord reservasjonen skal bruke for optimale resultater.

## Avvik og hindringer
Jeg holdt meg OK på planen, men selvfølgelig ble det avvik og hindringer her og der. Jeg hadde ikke den beste planen, så det var en del ting jeg måtte legge til eller fjerne.
- Sikkerhet: Jeg hadde ikke noe særlige planer for sikkerhet, men det jeg begynte med var OrgUnit struktur. Dette fant jeg ut av senere at ikke gidde helt mening, del av grunnen til det er at Org Units fokuserer på hierarki, men det er ikke veldig nødvendig, og jeg tror det hadde lagt til ekstra unødvendig arbeid. Da lagde jeg en egen tabell for custom sikkerhet, men dette var ikke god practice. Jeg prøvde å legge til org units logikk inni denne custom sikkerheten, men da ble det helt unødvendig rot. Til slutt endte jeg opp med å bruke en sikkerhetsmodell som var litt lik planen for custom sikkerheten, men der brukte jeg capabilities i stedenfor, og det tror jeg funker fint nok.
- Reservations Holders: Jeg la til en tab i Admin sida hvor en kan se alle som har hatt en reservasjon. Dette er fordi den kan være veldig nyttig for å ha oversikt, og gir admin mulighet for å anonymisere noen hvis det trengs. Jeg lagde også et view for dette som ikke var inkludert i planen.
- Lagt til tabell som ikke var med i planen: Uptimes. Denne var egentlig en veldig viktig del for restauranten, siden ellers hadde restauranten vært oppe hver dag og natt.
- Fjernet view Reservations Today: Dette var fordi jeg hadde allerede et view (som var med i planen): All Reservations som egentlig var akkurat det samme, så da brukte jeg det viewet med et simpelt filter i frontenden.
- En ting som tok meg litt for lang tid var kalkulasjonen av bord som en reservasjon skulle ta. Jeg fikk en endring, som var det at det måtte være spesifikke bord. For å ta høyde for dette måtte jeg kunne kalkulere bord som passet best antall gjester, og om det er for få plasser igjen. Dette virker fint nå, men var noe jeg brukte litt for lang tid på.
