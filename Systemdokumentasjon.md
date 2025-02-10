# Systemdokumentasjon

## Oppgave
Oppgaven er å lage et system for en restaurant (og kundene deres), hvor restauranten kan se alle reservasjoner, og kundene skal kunne lage reservasjoner, se dem, og kunne kansellere dem.

## Universell Utforming
Jeg har brukt grids som er greie til å navigere i for de fleste, men det kan være litt slit å holde på å trykke på en liten rute for noen. Da har jeg prøvd å få til slik at det blir brukt modaler og knapper der mulig for lettere interaksjon. I tillegg vil dette gjøre det lettere å forstå hvordan en gjør ting.

## Sikkerhet !
Her har jeg brukt noe som vi kaller Capabilities. Jeg har to capabilities: IsAdmin og IsCustomer. (Forklar hvordan de er tilgitt.) I SQL er det innebygde views som tillatter deg lett å sjekke hvilke capabilities noen har tilgang til. Jeg har da laget et view som er spesifisert mot dette systemet, som rett og slett returnerer om du har IsAdmin eller IsCustomer capabilitien, som gjør sikkerheten meget lett å håndtere.
I sikkerhets viewet til tabellene sjekker jeg om du har tilgang til tabellen (via et annet innebygd view som returnerer alle tabeller du har tilgang til via modulene nevnt tidligere), og jeg sjekker også opp mot om du har IsAdmin eller IsCustomer capabilities. Der blir det også litt mer custom basert på tabell. For eksempel: Admin skal ha tilgang til alle reservasjonene, men Customer skal bare ha tilgang til sine egne reservasjoner; men, hvis vi tenker på for eksempel åpningstider, da skal både Admin og Customer kunne se alt.
Vi bruker også mye triggere, som kjører sikkerhetssjekk omtrent likt som sikkerhets viewet til tabellene. Disse triggerene er da sjekker og logikk som kjører etter INSERT, UPDATE eller DELETE av data i spesifikke tabeller. Da må jeg, likt som i sikkerhets viewet til tabellene, legge til en sjekk på om du har tilgang til tabellen, men i tillegg til det, må jeg sjekke om de har Edit eller Delete permissions, kommer ann på hvilken trigger. I tillegg til det, likt som sikkerhets viewet til tabellene, må jeg sjekke opp om de er Admin eller Customer, og bruke logikk på hva Admin skal kunne gjøre og hva Customer skal kunne gjøre.
