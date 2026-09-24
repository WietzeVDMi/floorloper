# Floorloper

Interactieve rondleiding door een kantoorverdieping voor toekomstige huurders. Je loopt vanaf de lift door de gangen en ziet per ruimte of hij vrij, onder optie, verhuurd of gedeeld is.

- `index.html`: 3D-weergave (Three.js). Bekijk de verdieping van bovenaf of loop rond op ooghoogte.
- `plattegrond.html`: platte 2D-plattegrond met dezelfde gegevens.

## Concept

De verdieping is ingericht als flexibel kantoorconcept met hospitality voorop, naar het model van aanbieders als Co-Office:

- **Alles all-in**: één prijs per maand inclusief servicekosten, internet, koffie en thee, schoonmaak, host en receptie, gebruik van lounge en events. Volledig ingericht. Contract vanaf 3 maanden, daarna maandelijks opzegbaar.
- **Van flexplek tot teamkantoor**: flexplek (2 dagen per week), vaste werkplek (24/7), eigen kantoor, teamkantoor, en virtueel kantoor zonder werkplek.
- **Groeien zonder te verhuizen**: bij elk vrij kantoor staan de aangrenzende vrije ruimtes, zodat een huurder kan uitbreiden in hetzelfde gebouw.
- **Community**: de lounge met bar en lunchtafel is het hart van de verdieping, met een eventruimte voor lunches, sessies en borrels.

## Wat je kunt doen

- **Van boven**: draaien en zoomen rond het model. Klik op een ruimte en de bezoeker loopt erheen.
- **Rondlopen**: kijk rond op ooghoogte. Sleep om rond te kijken, loop met de pijltjestoetsen of WASD, of gebruik de knoppen linksonder op een telefoon. Klik op een vloer om er automatisch heen te lopen. Je kunt niet door muren lopen.
- **Rondleiding**: loopt langs alle ruimtes die vrij of onder optie zijn.
- **Minikaart** rechtsboven laat zien waar je bent en welke kant je op kijkt. Klik erop om naar een ruimte te lopen.
- **Details per ruimte**: all-in prijs per maand en per werkplek, oppervlakte, beschikbaar per, loopafstand vanaf de lift en uitbreidingsmogelijkheden.
- **Coworking**: klik op een bureau voor die vaste werkplek. Groen is vrij, grijs verhuurd, blauw is de flexzone.
- **Events**: het overzicht toont de events van deze week; klik erop en je loopt naar de ruimte.
- **Mijn selectie**: zet kantoren en vaste werkplekken in een selectie met het totaal all-in per maand. Die wordt in de browser bewaard (localStorage).

## Starten

Open `index.html` in de browser, er is geen build-stap nodig. Three.js wordt van cdnjs/jsdelivr geladen, dus je hebt internet nodig.

Met Docker:

```bash
docker compose up -d --build
```

Open daarna http://localhost:8791. GitHub Actions bouwt bij elke push naar `main` een image naar `ghcr.io/wietzevdmi/floorloper`.

## Gegevens aanpassen

Beschikbaarheid, huurprijzen en datums zijn **voorbeeldgegevens**. Ze staan bovenaan het script in beide HTML-bestanden:

- `PRICE`, `CONTRACT`, `INCLUDED`, `VAST_BEZET` en `EVENTS`: prijzen, contractvoorwaarden, wat inbegrepen is, welke vaste werkplekken bezet zijn en de events van de week.
- `north`: de ruimtes van de noordvleugel (positie in tekeneenheden van 5 cm, deur, status, beschikbaar per, tekst).
- `southOverride`: de zuidvleugel wordt gespiegeld van de noordvleugel; hier staan de afwijkende namen en statussen.

Status is `vrij`, `optie` of `verhuurd` voor kantoorruimtes. Ruimtes met `type: 'cowork'` (coworking), `type: 'gedeeld'` (vergaderkamers, lounge, eventruimte; met `bookable: true` per uur te reserveren) of `type: 'algemeen'` (toiletten, trappen, pantry) hebben geen huurstatus.
