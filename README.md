# KartTime Reader WebApp 3.1

Dit is de webapp-versie van KartTime Reader.

## Belangrijk: GitHub Pages alleen werkt NIET voor deze app

De fout:

    Unexpected token '<', "<html> <he"... is not valid JSON

ontstaat wanneer `/api/read` niet door de Node-server wordt uitgevoerd. GitHub Pages stuurt dan `index.html` terug. De frontend verwacht JSON en probeert vervolgens die HTML als JSON te lezen.

KartTime Reader heeft een backend nodig omdat Playwright de Apex Timing-pagina server-side moet openen.

## Lokaal testen

```bash
npm install
npx playwright install chromium
npm start
```

Open daarna:

```text
http://localhost:3000
```

## Online

Gebruik een Node-host die Playwright kan draaien, bijvoorbeeld Render.

Deze map bevat al `render.yaml`.

Na het online zetten krijg je bijvoorbeeld:

```text
https://jouw-karttime-reader.onrender.com
```

Als je de frontend apart op GitHub Pages zet, open dan:

`public/config.js`

en zet:

```js
window.KARTTIME_CONFIG = {
  API_BASE: "https://jouw-karttime-reader.onrender.com"
};
```

De frontend praat dan met de online backend.

## Nog eenvoudiger

Je kunt ook de volledige map als één Node-app deployen. Dan staan frontend en backend op dezelfde URL en hoeft `API_BASE` leeg te blijven.

## Functies

- Apex Timing-link invoeren
- live timing uitlezen
- kartnummers automatisch herkennen
- zichtbare beste rondetijd gebruiken
- huidige/laatste lap niet als beste tijd gebruiken
- drivernaam proberen te herkennen
- sessie/heat/fase herkennen
- heats opslaan
- beste tijd per kart
- gemiddelde per kart
- aantal opgeslagen heats
- ranking met 70% gemiddelde + 30% beste tijd
- karts verwijderen
- automatisch opnieuw uitlezen
- lokale opslag in de browser
