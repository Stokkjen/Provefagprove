# Oppgave
## Mål
Målet med oppgaven er å lage en app for å ha kontroll på reservasjoner for en restaurant, og for gjestene å legge til eller kansellere reservasjoner. Denne restauranten kan kun ha 12 gjester til gangen, men det ble ikke spesifisert noe med hvordan bordene virker. Da tar jeg og antar at de setter i sammen bord som har plass til 2 stykk sammen, slik at hvis det er 4 blir det 2 bord, hvis det er 5 blir det 3 bord. De har 6 bord, som gjør slik at 12 gjester holder maksimum. Men, det kan hende at alle bordene blir brukt og det ikke er hele 12 gjester.

# Arbeid
## Fremgangsmåte:
- Først vil jeg bruke DrawSQL for å tenke opp og illustrere en datamodell (hovedsaklig tabeller) som tilpasser selve oppgaven.
- Jeg kommer også til å tenke ut eventuelle views for å få samlet data på en sikker og fornuftig måte.
- Det samme gjelder for prosedyrer, for å få funksjonaliteten som er nødvendig.
- Så kommer jeg til å lage illustrasjoner av appene ved hjelpen av Figma.
- Når jeg har en klar idé over hvordan ting skal fungere og se ut, begynner jeg med å definere alle objektene i SQL. Dette inkluderer da tabeller, views og procedures.
- Da skal backend delen være på plass, men hvis nødvendig, gjør jeg modifikasjoner til triggerene for å få på plass spesifikke tilganger eller funksjonalitet rundt modifisering av data i tabeller.
- Da begynner jeg å jobbe på frontend delen. Da følger jeg bare Figma skissen, og tar i bruk views og prosedyrer som jeg har laget.
- Hvis nødvendig kan det hende at jeg går tilbake senere å gjør småendringer hvis noe dukket opp.
- Når jeg er ferdig med det og hvis jeg får tid, er det egentlig hovedsaklig bare for meg å legge til noen bonuser hvis jeg får tid til det.
- Når presentasjonen nærmer seg begynner jeg å forberede meg.
## Timeplan
### 05.02.25 - Onsdag (7.5t):
- Gjennomgang av prøvefagprøve.
- Dikte opp og illustrere datamodell ved hjelp av DrawSQL.
- Dikte opp og illustrere apps ved hjelp av Figma.
- Dikte opp og notere ned views og prosedyrer som er nødvendige/fornuftig.
- Planlegge utviklingen.
- Lever inn planlegging.
### 06.02.25 - Torsdag (7.5t):
- Definere tabeller som finnes i datamodellen.
- Begynne på å definere views og prosedyrer og evt. jobbe med triggere, men basert på hvor mye det blir, kan dette nok drøye seg ut til neste dag.
### 07.02.25 - Fredag (7.5t):
- Fullføre backenden.
- Begynne på appene ved å følge skissen laget i Figma.
### (08-09).02.25 - Helg:
- Fortsette på appene.
### 10.02.25 - Mandag (7.5t):
- Fortsette på appene.
- Evt. modifiser på backenden hvis ting har dukket opp.
### 11.02.25 - Tirsdag (7.5t):
- Test test test, fiks fiks fiks.
- Fullfør appene.
- Forberede seg til presentasjon.
### 12.02.25 - Onsdag:
- Presentasjon
### Kostnad:
- Total timekostnad: 5812.50,-
  - Antall timer: 37.5
  - Timekostnad: 155,-
- Omega365 lisens (Per måned):
  - Hosting: 8000,-
  - Produkt: 25000,-
  - Bruker: 380,-
- Total kostnad: 38812.50,- (pluss 380,- per bruker)

# Teknologi
## Omega365:
- CTP - ellers kjent som "Core Technology Platform" er passende, siden den holder seg godt oppdatert, og bruker Vue.js, som er et rammeverk som støtter gjenbrukbare komponenter, og har mange innebygde komponenter allerede.
- Appdesigner - lar deg lage appene. Her får du mange kjekke verktøy som du kan bruke for vise frem data, og å gjøre endringer.
- Code Search - lar deg se på koden i andre apper. Dette er et meget kjekt verktøy å bruke når en ikke husker eller ikke vet hvordan en bruker spesifikke komponenter eller hvis du vil vite hvordan en gjør ting i javascript.
- Snippets - litt lik code search, men mer oversiktlig og klar. Snippets lar deg lese dokumentasjon om spesifikke komponenter, f.eks hvilken propper de har og hva de gjør.
- Data API - tillater deg å kommunisere fra frontend til backend. Ved hjelp av dataobjekter kan du koble til views. (Ikke tabeller. Det beste du kan koble til er tabell view, et view som er designet for å vise tabellen med sikkerhet integrert.) Den kan også kjøre prosedyrer.
## Annet:
- Github - for dokumentasjon. Er veldig simpelt og greit.
- DrawSQL - for å lage datamodell.
- Figma - for å tegne hvordan appene skal omtrent se ut.

# Skisser
## Datamodell ([DrawSQL](https://drawsql.app/teams/omega365-1/diagrams/datamodell-for-restaurant-reservasjoner))
Fikk dessverre ikke tid til å legge inn skikkelig sikkerhet, men det kommer.
![image](https://github.com/user-attachments/assets/acb22cf1-3e13-4d70-b4f6-7c4bd53ea59d)
- Reservations: Holder informasjon om alle reservasjoner.
- ReservationHolder: Informasjon om forskjellige folk som har booket reservasjon. De kan enten være allerede i systemet, eller så kan det være at de ble lagt til av admin.
## Apps ([Figma](https://www.figma.com/design/kMkTUjpAfLm7iCGBfJY29F/Untitled?node-id=0-1&t=NluZZ85m8prvQAlU-1))
![image](https://github.com/user-attachments/assets/d715d876-e5d4-4c97-8b1a-081f92dc46a7)

# Views, Procedures og Triggers
## Views
- AllReservations: Viser alle reservasjoner for admin.
- ReservationsToday: Viser alle reservasjoner som er i dag. Disse skal være hovedfokuset for admin.
## Procedures
- BookReservation: Booker reservasjon. Denne tar inn reservasjoner fra både admin og kunde.
  - Kansellering kunne hatt en prosedyre, men det kan en gjøre i gridden. Dette er da en mulig utvidelse om jeg får tid.
## Triggers
- Reservations Insert: Hvis inserten ender opp med mer enn 6 bord opptatt, stopper triggeren deg.

# Kilder
## Informasjonskilder:
- [ChatGPT](https://chatgpt.com/)
- [StackOverflow](https://stackoverflow.com/)
- [Vue.js](https://vuejs.org/)
- [W3Schools](https://www.w3schools.com/)
- [Bootstrap Docs](https://getbootstrap.com/docs/5.3/getting-started/introduction/)
- [Figma](https://www.figma.com/)
- [DrawSQL](https://drawsql.app/)
## Samarbeidspartnere:
- Det kan hende jeg bruker Tor, mest sannsynlig relatert til sikkerhet eller noe backend greier.
- Kolleger, sikkert for frontend greier.
