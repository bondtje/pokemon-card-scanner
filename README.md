# Pokémon Card Scanner

Een single-page web-app die een Pokémon-kaart via de (telefoon)camera fotografeert,
de **naam** en het **kaartnummer** via OCR (Tesseract.js) leest, de kaart opzoekt via
de [pokemontcg.io](https://pokemontcg.io) API en de **waarde in euro's** toont
(Cardmarket in €, TCGplayer omgerekend van $).

## Gebruik
Open `index.html` via **HTTPS** (de camera werkt niet op `file://` of gewoon `http://`).
Via GitHub Pages krijg je automatisch een https-URL.

## GitHub Pages aanzetten
1. Push deze map naar een GitHub-repo.
2. Repo → **Settings → Pages** → *Build and deployment* → Source: **Deploy from a branch**.
3. Branch: **main**, map: **/(root)** → **Save**.
4. Na ~1 minuut staat de app op `https://<gebruiker>.github.io/<repo>/`.

## Werking
- 📸 **Scan kaart** maakt een scherpe foto en analyseert die (geen continue scan).
- De **naam** (grote tekst) stuurt de zoekopdracht; het **nummer** filtert de juiste versie.
- Resultaten tonen afbeelding, type, rarity (holo/alt art), HP, illustrator en prijzen.
