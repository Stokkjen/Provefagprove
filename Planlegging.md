# Oppgave
## Mål
Målet med oppgaven er å lage en app for å ha kontroll på reservesjoner for en restaurant. Denne restauranten kan kun ha 12 gjester til gangen, men det ble ikke spesifisert noe med hvordan bordene virker. Da tar jeg og antar at de setter i sammen bord som har plass til 2 stykk sammen, slik at hvis det er 4 blir det 2 bord, hvis det er 5 blir det 3 bord, og de har da 6 slike bord, som gjør slik at 12 gjester holder maksimum. Men, det kan hende at alle bordene blir brukt og det ikke er hele 12 gjester.

# Arbeid
## Fremgangsmåte:
- Først vil jeg bruke DrawSQL for å tenke opp og illustrere en datamodell (hovedsaklig tabeller) som tilpasser selve oppgaven.
- Jeg kommer også til å tenke ut eventuelle views for å få samlet data på en sikker og fornuftig måte.
- Det samme gjelder for prosedyrer, for å få funksjonaliteten som er nødvendig.
- Så kommer jeg til å lage illustrasjoner av appene som kreves, inkludert knapper, modaler, gridder og hva enn som trengs.
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
- Dikte opp og illustrere app(s) ved hjelp av Figma.
- Dikte opp og notere ned views og prosedyrer som er nødvendige/fornuftig.
- Planlegge utviklingen og 
- Lever inn planlegging.
### 06.02.25 - Torsdag (7.5t):
- Definere tabeller som finnes i datamodellen.
- Begynne på å definere views og prosedyrer og evt. jobbe med triggere, men basert på hvor mye det blir, kan dette nok drøye seg ut til neste dag.
### 07.02.25 - Fredag (7.5t):
- Fullføre backenden.
- Begynne på appen ved å følge skissen laget i Figma.
### (08-09).02.25 - Helg:
- Fortsette på appen.
### 10.02.25 - Mandag (7.5t):
- Fortsette på appen.
- Evt. modifiser på backenden hvis ting har dukket opp.
### 11.02.25 - Tirsdag (7.5t):
- Test test test, fiks fiks fiks.
- Fullfør appen.
- Forberede seg til presentasjon.
### 12.02.25 - Onsdag:
- Presentasjon
### Kostnad:
- Timer: 37.5
- Timekostnad: 155kr
- Totalkostnad: 5812,5kr

# Teknologi
## Omega365:
- Appframe - Omega365 sitt rammeverk. Dette er det jeg valgte, siden jeg kjenner meg godt igjen der. Det finnes mange verktøy innebygd.
- CTP - ellers kjent som "Core Technology Platform" er passende, siden den holder seg godt oppdatert, og bruker Vue.js, som er et rammeverk som støtter gjenbrukbare komponenter, og har mange innebygde komponenter allerede.
- Appdesigner - lar deg lage appene. Her får du mange kjekke verktøy som du kan bruke for vise frem data, og å gjøre endringer.
- Code Search - lar deg se på koden i andre apper. Dette er et meget kjekt verktøy å bruke når en ikke husker eller ikke vet hvordan en bruker spesifikke komponenter eller hvis du vil vite hvordan en gjør ting i javascript.
- Snippets - litt lik code search, men mer oversiktlig og klar. Snippets lar deg lese dokumentasjon om spesifikke komponenter, f.eks hvilken propper de har og hva de gjør.
- Data API - tillater deg å kommunisere fra frontend til backend. Ved hjelp av dataobjekter kan du koble til views. (Ikke tabeller. Det beste du kan koble til er tabell view, et view som er designet for å vise tabellen med sikkerhet integrert.) Den kan også kjøre prosedyrer.
## Annet:
- Jeg kommer til å bruke internettet for å finne ut av syntax i kode og debugging og litt andre greier som kan være greit.
- Det kan hende jeg bruker Tor eller kolleger.
- Det er en mulighet for at jeg bruker ChatGPT for lik grunn som internettet.

# Skisser
## Databasemodell (DrawSQL)
INSERT IMAGE HERE
- Tabell 1: Beskrivelse.
## App (Figma)
INSERT IMAGE HERE
