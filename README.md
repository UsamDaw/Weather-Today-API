# Værmeldingsnettside

Dette er en enkel værmelding nettside som lar brukere hente gjeldende værforhold og en 24 timers værmelding for enhver by. Den henter data fra [OpenWeatherMap API](https://openweathermap.org/api) og viser værinformasjon, temperatur, værbeskrivelse og timevarsel.

## Funksjoner
- Få aktuell værinformasjon for en valgt by.
- Vis temperatur, værforhold og et tilsvarende værikon.
- Hent og vis et 24 timers værvarsel med temperatur og værforhold.
- Feilhåndtering for ugyldig byinndata og APIhentingsfeil.

## API-bruk

Nettsiden bruker OpenWeatherMap API for både gjeldende værdata og prognosedata. Slik brukes API-en:

1. **Gjeldende vær-API:**
 – Endepunkt: `https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apiKey}`
 - Dette endepunktet henter gjeldende vær for den gitte byen.

2. **Weather Forecast API:**
 – Endepunkt: `https://api.openweathermap.org/data/2.5/forecast?q={city}&appid={apiKey}`
 – Dette endepunktet henter værmeldingsdataene for de neste dagene, men nettsiden bruker foreløpig kun de første 10 oppføringene (24 timer).

## Hvordan det fungerer
1. Brukeren legger inn et bynavn.
2. Hvis bynavnet mangler, varsler nettsiden brukeren om å skrive inn et bynavn.
3. nettsiden foretar deretter to API-kall:
 - En for det aktuelle været.
 - En for prognosen (24-timers data hentes).
4. Dataene som returneres fra disse API-kallene, vises på siden:
 - Gjeldende temperatur (konvertert fra Kelvin til Celsius).
 - Beskrivelse av været (f.eks. overskyet, klart).
 - Et værikon som representerer gjeldende forhold.
 - Timevarsel som viser temperatur- og værikoner for de neste 24 timene.

## Kodesammenbrudd

### `getWeather()`
Denne funksjonen:
- Får bynavnet fra brukeren.
- Henter både gjeldende vær- og prognosedata ved hjelp av OpenWeatherMap API.
- Hvis det lykkes, kaller det `displayWeather()` for å vise gjeldende vær og `displayHourlyForecast()` for å vise 24-timersvarselet.
- Håndterer eventuelle API-feil og varsler brukeren hvis noe går galt.

### `displayWeather(data)`
Denne funksjonen:
- Tar gjeldende værdata fra API-svaret.
- Trekker ut og viser bynavn, temperatur (i Celsius), værbeskrivelse og et ikon som representerer været.
- Kaller `showImage()` for å gjøre værikonet synlig.

### `displayHourly Forecast(hourlyData)`
Denne funksjonen:
- Tar timeprognosedata fra API.
- Trekker ut de første 10 timene (neste 24 timer med prognose).
- Viser varslede temperatur- og værikoner for hver time.

### `showImage()`
Denne funksjonen:
- Viser værikonet når gjeldende værdata er hentet.

## Installasjon og oppsett
1. Klon depotet eller last ned kildekoden.
2. Åpne HTML-filen i nettleseren din.
3. Skriv inn bynavnet og trykk enter for å få værdetaljer.

**Merk:** Sørg for å erstatte plassholderen "apiKey" med din faktiske OpenWeatherMap API-nøkkel.

## Utfordringer
Noen utfordringer under utviklingen av denne nettsiden:
- Konvertering av temperatur fra Kelvin til Celsius, ettersom OpenWeatherMap API returnerer temperaturer i Kelvin som standard.
- Håndtere feil på en elegant måte, for eksempel ugyldige bynavn eller API-forespørselsfeil.

## Fremtidige forbedringer
- Legg til funksjonalitet for å vise mer detaljert prognoseinformasjon (f.eks. ukentlig prognose).
- Forbedre brukeropplevelsen ved å legge til lasteindikatorer under API-forespørslene.
- Legg til flere lokaliseringsalternativer, for eksempel å hente værdata på forskjellige enheter eller språk.
<br />

## Rikitig bruk av fargekontrast
![image_alt](https://github.com/UsamDaw/Weather-Today-API/blob/main/ColorAdobeExample.png?raw=true)

## Kontrastforhold av Adobe color
![image_alt](https://github.com/UsamDaw/Weather-Today-API/blob/main/Screenshot%202024-10-09%20123641.png?raw=true)


## Mangelfull bruk av fargekontrast
![image alt](https://github.com/UsamDaw/Weather-Today-API/blob/main/ColorAdobeExample2.png?raw=true)

### Kontrastforhold av Adobe color
![image_alt](https://github.com/UsamDaw/Weather-Today-API/blob/main/Screenshot%202024-10-09%20125832.png?raw=true)

#### Du kan bruke fargekontrast analysatoren som er tilgjengelig på https://color.adobe.com/create/color-contrast-analyzer for å vurdere synligheten til farger for brukerne av nettstedet ditt.
