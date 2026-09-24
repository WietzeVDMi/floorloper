# Floorloper

Interactieve rondleiding door een kantoorverdieping voor toekomstige huurders. Je loopt vanaf de lift door de gangen en ziet per ruimte of hij vrij, onder optie, verhuurd of gedeeld is.

- `index.html`: 3D-weergave (Three.js). Bekijk de verdieping van bovenaf of loop rond op ooghoogte.
- `plattegrond.html`: platte 2D-plattegrond met dezelfde gegevens.

## Wat je kunt doen

- **Van boven**: draaien en zoomen rond het model. Klik op een ruimte en de bezoeker loopt erheen.
- **Rondlopen**: kijk rond op ooghoogte. Sleep om rond te kijken, loop met de pijltjestoetsen of WASD, of gebruik de knoppen linksonder op een telefoon. Klik op een vloer om er automatisch heen te lopen. Je kunt niet door muren lopen.
- **Rondleiding**: loopt langs alle ruimtes die vrij of onder optie zijn.
- **Minikaart** rechtsboven laat zien waar je bent en welke kant je op kijkt. Klik erop om naar een ruimte te lopen.
- **Details per ruimte**: oppervlakte, werkplekken, huur en servicekosten, beschikbaar per en loopafstand vanaf de lift.
- **Shortlist**: zet ruimtes op een lijstje. Die wordt in de browser bewaard (localStorage).

## Starten

Open `index.html` in de browser, er is geen build-stap nodig. Three.js wordt van cdnjs/jsdelivr geladen, dus je hebt internet nodig.

Met Docker:

```bash
docker compose up -d --build
```

Open daarna http://localhost:8791. GitHub Actions bouwt bij elke push naar `main` een image naar `ghcr.io/wietzevdmi/floorloper`.

## Gegevens aanpassen

Beschikbaarheid, huurprijzen en datums zijn **voorbeeldgegevens**. Ze staan bovenaan het script in beide HTML-bestanden:

- `north`: de ruimtes van de noordvleugel (positie in tekeneenheden van 5 cm, deur, status, beschikbaar per, tekst).
- `southOverride`: de zuidvleugel wordt gespiegeld van de noordvleugel; hier staan de afwijkende namen en statussen.
- `RENT` en `SERVICE`: huur en servicekosten in euro per m² per maand.

Status is `vrij`, `optie` of `verhuurd` voor kantoorruimtes. Ruimtes met `type: 'gedeeld'` (vergaderkamers) of `type: 'algemeen'` (toiletten, trappen, pantry) hebben geen huurstatus.
