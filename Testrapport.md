![image](https://github.com/user-attachments/assets/56ad7524-55af-473f-8cc2-3cbce5fdeb80)# Testrappport
## Ny Reservasjon
<table>
  <th>Funksjon</th>
  <th>Forventning</th>
  <th>Bilde(r)</th>
  <th>Hva skjedde?</th>
  <th>Status</th>
  <tr>
    <td>For mange gjester</td>
    <td>Når en reserverer for mange gjester skal det komme opp en klar feilmelding.</td>
    <td><img src="https://github.com/user-attachments/assets/60266d9e-c0bd-4d25-88c3-ec76950e98d6"/></td>
    <td>En feilmelding med informasjon om hva som gikk feil kom opp.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Utanfor restaurantens tider</td>
    <td>Når en reserverer utanfor åpentidene til restauranten skal det komme opp en klar feilmelding.</td>
    <td><img src="https://github.com/user-attachments/assets/55b315aa-ca29-43a9-b009-f772060738cc"/></td>
    <td>En feilmelding med informasjon om hva som gikk feil kom opp.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Oppretting av reservasjon</td>
    <td>Oppretting av reservasjon virker fint, og lager reservasjonen.</td>
    <td></td>
    <td>Dette gikk fint. Modalen lukker, og appen (customer og admin) laster inn den nye reservasjonen.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Reservasjons holder</td>
    <td>Når en oppretter en reservasjon (som admin) med et nytt navn og telefon nummer skal den nye informasjonen bli lagt til i Reservations Holders.</td>
    <td><img src="https://github.com/user-attachments/assets/48cbf0c8-2dc4-4746-8dd4-f863b5d902f8"/>
        <img src="https://github.com/user-attachments/assets/38486027-d734-4c3d-a2b0-d2e4628b782b"</td>
    <td>Holderen blir lagt til som en holder, og informasjonen er korrekt.</td>
    <td>✅</td>
  </tr>
</table>

## Customer
<table>
  <th>Funksjon</th>
  <th>Forventning</th>
  <th>Bilde(r)</th>
  <th>Hva skjedde?</th>
  <th>Status</th>
  <tr>
    <td>Kansellering skjules</td>
    <td>Kansellering skal kansellere og skjule reservasjon til standard, så lenge "Include Cancel" er av.</td>
    <td><img src="https://github.com/user-attachments/assets/772910dd-5154-43ad-82b3-4323dd7740fe"/>
        <img src="https://github.com/user-attachments/assets/6c1d710c-f658-4fde-a1ca-67dc70bca4c8"/></td>
    <td>Kansellerings knappen kansellerer og skjuler reservasjon. Når jeg trykker "Include Cancelled", vises den.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Bare kansellere fremtidige reservasjon</td>
    <td>Det skal bare være mulig å kansellere reservasjoner frem i tid, ikke i dag eller i går.</td>
    <td><img src="https://github.com/user-attachments/assets/6956cde1-debe-405d-b51a-58b405258a45"/></td>
    <td>Kanselleringsknappen forsvinner når i dag eller tidligere (dette ble testet 11/02/2025).</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>New Reservation reloader grid</td>
    <td>Når en lager en ny reservasjon via New Reservation modalen skal gridden reloade for å vise den nye reservasjonen.</td>
    <td></td>
    <td>Gridden reloader med en gang en lager reservasjonen.</td>
    <td>✅</td>
  </tr>
</table>

## Admin
<table>
  <th>Funksjon</th>
  <th>Forventning</th>
  <th>Bilde(r)</th>
  <th>Hva skjedde?</th>
  <th>Status</th>
  <tr>
    <td>Kansellering skal skjule</td>
    <td>Kansellering skal kansellere og skjule reservasjon til standard, så lenge "Include Cancel" er av.</td>
    <td></td>
    <td>Kansellerings knappen kansellerer og skjuler reservasjon. Når jeg trykker "Include Cancelled", vises den.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Bare kansellere fremtidige reservasjon</td>
    <td>Det skal bare være mulig å kansellere reservasjoner frem i tid, ikke i dag eller i går.</td>
    <td><img src="https://github.com/user-attachments/assets/57d91656-b784-4112-93e5-7b0f05504ede"/></td>
    <td>Kanselleringsknappen forsvinner når i dag eller tidligere (dette ble testet 11/02/2025.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Hide/Show</td>
    <td>Knapp under felt "Action" skal endre mellom "Hide" og "Show" basert på om den er skjult eller ikke.</td>
    <td><img src="https://github.com/user-attachments/assets/2b95288a-f612-413b-a70e-6676fb17ced9"/></td>
    <td>Knappen endrer seg basert på kolonne "Hidden", og virker som forventet.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Anonymize</td>
    <td>Anonymize knapp bør skjule bruker (selv om "Include Hidden" er på), og fjerne navn og telefon.</td>
    <td><img src="https://github.com/user-attachments/assets/847c1def-87a7-46e0-af30-cfcb69ee87ac"/>
        <img src="https://github.com/user-attachments/assets/db508c9b-f35b-4817-b0b0-4eec3ca2597b"/></td>
    <td>Når jeg trykket "Anonymize" knappen og bekreftet advarselen, forsvant den med en gang, selv om jeg har "Include Hidden" på. Navn og Telefon ble tom i databasen.</td>
    <td>✅</td>
  </tr>
  <tr>
    <td>New Reservation reloader grid</td>
    <td>Når en lager en ny reservasjon via New Reservation modalen skal alle griddene som har relasjon bli reloaded.</td>
    <td></td>
    <td>Når jeg lager en ny reservasjon med ny holder, reloades All Reservations grid og Reservations Holders grid, som gjør slik at når jeg blar til dem etterpå så er de allerede lastet inn.</td>
    <td>✅ Måtte stoppe Today's Reservations fra å loade, fordi det er ikke mulig å lage en reservasjon for i dag.</td>
  </tr>
</table>
