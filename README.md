# Pokémon Card Scanner

Een single-page web-app om Pokémon-kaarten te scannen met de (telefoon)camera, hun
**waarde** op te zoeken, een **collectie** bij te houden en een **officiële decklist**
af te drukken voor toernooien.

**Live:** https://bondtje.github.io/pokemon-card-scanner/

> De camera werkt alleen via **HTTPS** (GitHub Pages levert dat). Lokaal openen via
> `file://` werkt niet voor de camera.

## Tabbladen

### 📷 Scanner
- Maakt een **scherpe foto** van de kaart en analyseert die (geen wazige live-scan).
- **Volledige-kaart OCR** (Tesseract.js): leest de hele kaart, niet één vast vakje.
  - **Naam**: vergelijkt elk woord met de echte Pokémon-namenlijst (PokéAPI) en kiest
    de beste match; bij twijfel verschijnen **suggestie-chips** mét het unieke nummer.
  - **Nummer**: zoekt het patroon `055/078` overal in de tekst (zwart-wit/Otsu-verwerkt).
- **Zoeken op naam + uniek nummer** (apart nummer-veld) om de juiste versie te vinden.
- Werkt op pc én gsm; knop om **van camera te wisselen** (voor- / achtercamera).
- Resultaten tonen afbeelding, type, rarity (holo / alt art / secret), HP, illustrator,
  **Cardmarket-prijs in €** en **TCGplayer-prijs in $**.

### 📚 Collectie
- **➕ Toevoegen aan collectie** bij elk zoekresultaat (aantallen tellen op).
- Overzicht met totaal aantal kaarten, aantal unieke en **totale waarde (Cardmarket €)**.
- Per kaart: aantal **+/−** en verwijderen.
- **Export / Import** als JSON-back-up.
- Opgeslagen lokaal in de browser (**localStorage**) — per apparaat/browser.
- **🖨️ Afdrukken**: nette kaartlijst, gegroepeerd in Pokémon / Trainer / Energy,
  met een afvink-kolom.

### 📋 Decklist (officieel formaat)
- **Meerdere decks**: maak, hernoem, dupliceer en verwijder decks, en kies via een
  dropdown welk deck actief is (elk deck wordt apart bewaard).
- Stel een toernooi-deck samen van **precies 60 kaarten**.
- **Spelergegevens**: naam, Player ID, geboortedatum, divisie (Masters/Senior/Junior).
- Voeg kaarten uit je collectie toe met een stepper (**max. 4** kopieën per kaart) en
  voeg **basis-energie** toe (Grass, Fire, Water, …).
- Live **60/60**-teller (groen als compleet).
- **🖨️ Afdrukken** in Play! Pokémon-stijl: spelerkop + tabellen voor
  Pokémon / Trainer / Energy met Aantal · Naam · Set · Nr, en een geldigheidscheck.
- Deck wordt lokaal bewaard (localStorage).

## Databronnen
- Kaartdata & prijzen: [pokemontcg.io](https://pokemontcg.io) (Cardmarket €, TCGplayer $).
- Namencorrectie: [PokéAPI](https://pokeapi.co).
- OCR: [Tesseract.js](https://tesseract.projectnaptha.com/).
- Officiële bronnen: [Cardmarket](https://www.cardmarket.com/en/Pokemon) ·
  [TCGplayer](https://www.tcgplayer.com/).

## Techniek
- Eén bestand: `index.html` (HTML + CSS + JS, geen build-stap).
- Geen server/database nodig; collectie en deck staan in `localStorage`.
- Print via `@media print` (alleen de lijst wordt afgedrukt; “Opslaan als PDF” kan ook).

## Ontwikkeling / deploy
Bron wordt bewerkt als `index.html`. Wijziging pushen naar `main` →
GitHub Pages bouwt de site automatisch opnieuw.

## Beperkingen / ideeën
- localStorage is per apparaat. Voor sync over meerdere apparaten is een online
  database nodig (bijv. Firebase/Supabase) — nog niet ingebouwd.
- Browser-OCR blijft beperkt bij klein/onscherp drukwerk; een foto bij goed licht en
  het handmatige naam-/nummerveld zijn de vangnetten.
