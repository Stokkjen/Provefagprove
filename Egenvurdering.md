# Egenvurdering
## Oppsumering
Jeg syns oppgaven gikk OK. Det var noen problemer jeg går dypere i under "Utfordringer", men generelt sett ville jeg si at jeg til slutt hadde en relativt OK løsning med OK sikkerhet, og hadde universell utforming og lovverk i tanken.
## Utfordringer
Det ble desverre en del utfordringer, spesielt med sikkerhet. Planleggingen min ble ganske svak, delvis fordi jeg tenkte å skrive hele planen før jeg faktisk satt meg ned å begynte på datamodellen og app skissene, som førte til at jeg måtte gjøre store endringer i planen, brukte alt for mye tid på å planlegge, og endte opp med en svak plan. Den neste utfordringen var kalkulasjon av hvordan bordene skulle bli utdelt til gjestene.

Selve presentasjonen failet i begynnelsen, grunnet feil med booking prosedyren. Dette inkluderer feil som UTC og bord som var disabled.

Jeg testet UTC-en, men bare på kveldstid. Det kom opp en feil når jeg prøvde å legge til en reservasjon på morgentid.

Jeg tror grunnen til at testingen for "opptatt bord" virket for meg, men det virket ikke når jeg presenterte, var fordi når jeg testet, brukte jeg for mange gjester selv om det var et ledig bord. Jeg hadde begynt med implementasjon for å kunne deaktivere og legge til bord, så jeg måtte legge til en sjekk i prosedyren min, men den ser ikke ut til å ha virket.
## Avvik
Grunnet en relativt svak plan, er det ikke mange direkte avvik jeg hadde. Jeg la til noen ting som var nødvendig, men ble ikke inkludert i planen:
- Reservations Holders tab - Denne la jeg til fordi da er det en lett måte for admin å kunne se alle som har reservert, og også en lett måte for dem å anonymisere (som er en annen ting som ikke var i planen).
- Uptimes - Denne burde ha vært inni planen, fordi dette er nødvendig funksjonalitet. Det holder informasjon om hvilke dager restauranten er oppe, og når.
- Det var også noe greier rundt bord funksjonalitet, men dette var grunnet twisten jeg fikk.

Jeg fjernet et view som jeg skulle ha med, som var "ReservationsToday", fordi der kunne jeg bare bruke "AllReservations" viewet og filtrere på hvor reservasjonen var i dag. Jeg fjernet også muligheten til å slette rader, og byttet det ut med "soft delete" omtrent over alt, spesielt hvor nødvendig. I systemdokumentasjonen finnes det mer informasjon av det meste her.
## Annerledes
- I planen burde jeg ha brukt mer tid på å få på plass datamodellen og skissene med en gang, i stedenfor å bruke masse tid på å lage plan, lage datamodellen, så endre på planen for å tilpasse.
- Jeg burde også ha tenkt på sikkerhet på forhånd, siden det kostet meg mye tid under den andre dagen, og litt den tredje.
- Bruke mindre tid på det unødvendige. Jeg hadde en plan for å kunne skru av og på bord, og kunne legge til bord, men dette tok meg ganske lang tid fordi det er mye en må ha tanke på når en gjør det, og det var ikke del av oppgaven, så jeg stoppet med det, og fjernet det.
