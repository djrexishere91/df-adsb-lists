# df-adsb-lists

## IMPORTANT / IMPORTANTE

**IT:** non modificare direttamente le liste “originali” su `main`.  
Se vuoi personalizzarle, fai una **copia locale** oppure un **fork** del repository e lavora sulla tua versione.  
Se vuoi proporre una correzione, apri una **Issue** o una **Pull Request**.

**EN:** do not edit the “original” lists on `main` directly.  
If you want to customize them, make a **local copy** or **fork** this repository and work on your own version.  
If you want to suggest a fix, open an **Issue** or a **Pull Request**.

---

## IT — Descrizione

Questo repository contiene liste **CSV** di aeromobili (identificati da ICAO **HEX**) con metadati e link (info + immagini).

Le liste vengono aggiornate in base ai rilevamenti della mia stazione ADS‑B, situata a **Fiscaglia (provincia di Ferrara), Italia**.

Sono pensate per essere consumate da bot/alert ADS‑B (es. notifiche Telegram), da dashboard personali o da strumenti di analisi (Python, Excel, Grafana, ecc.).

## IT — File disponibili (download “raw”)

Link diretti ai CSV (utili per `curl/wget` o import automatico):

- Military (MIL): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-mil-images.csv
- Government (GOV): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-gov-images.csv
- Police / Law enforcement (POL): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-pol-images.csv
- Helicopter EMS / “Flying Doctors” (FD): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-flyingdocs.csv
- Civil (curated) (CIV): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-civ-curated-images.csv

Tip: apri un file su GitHub e clicca **Raw** per ottenere l’URL diretto.

## IT — Utilizzi possibili (idee pratiche)

- Alert in tempo reale: confronta gli aeromobili “visti” dalla tua stazione ADS‑B (es. `aircraft.json`, Beast, SBS) con queste liste; quando l’HEX matcha, invia una notifica (Telegram/Discord/email).
- Arricchimento dati: se nel tuo feed hai solo HEX/callsign, puoi usare queste liste per aggiungere registrazione, operatore, tipo, link e immagini.
- Filtri e classificazione: usa `CMPG`, `Category` e `Tag1..Tag3` per creare filtri (es. solo “Gov”, solo “SAR”, solo “VVIP”).
- Analisi storica: unisci log/DB del tuo ricevitore con queste liste per statistiche (quanti passaggi per categoria, quali operatori, ecc.).
- Import “manuale”: apri i CSV con Excel/LibreOffice oppure importali in un DB (SQLite/Postgres) per fare query.

## IT — Esempi rapidi

Scaricare una lista in locale:

curl -L -o plane-alert-gov-images.csv
https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-gov-images.csv



Filtrare un HEX specifico:

grep -i "^06A3D5," plane-alert-gov-images.csv



Esempio “match” (pseudo‑codice):

seen_hex = stream_adsb_hex()
if seen_hex in csv_hex_list:
send_alert(seen_hex, metadata, img_url)



## IT — Formato CSV

Tutte le liste condividono lo stesso header (stesse colonne). Ogni riga rappresenta un aeromobile identificato da ICAO HEX (24-bit).

Colonne:
- HEX: ICAO 24-bit (es. `06A3D5`)
- Reg: registrazione (se nota)
- Operator: operatore/ente
- Type: descrizione modello (testo libero)
- ICAO Type: designatore ICAO (es. `B77L`, `A139`, ecc.)
- CMPG: categoria breve (es. Mil/Pol/Gov/Civ)
- Tag1 / Tag2 / Tag3: tag liberi (es. paese, reparto, callsign, note)
- Category: categoria testuale (libera)
- Link: URL informativo (FlightRadar24, Airfleets, Wikipedia, ecc.)
- Img1..Img4: URL immagini (fonti esterne)

Note:
- Alcuni campi possono essere vuoti.
- I link esterni possono cambiare nel tempo.

## IT — Note su immagini e link esterni

Le immagini e i link puntano a fonti esterne e restano soggetti ai rispettivi termini d’uso.  
Se un URL non è più valido, è normale: i siti possono modificare o rimuovere contenuti.

## IT — Licenza

Vedi `LICENSE` (MIT).

---

## EN — Overview

This repository contains **CSV** aircraft lists (identified by ICAO **HEX**) with metadata and links (info + images).

The lists are updated based on detections from my ADS‑B station located in **Fiscaglia (Ferrara province), Italy**.

They are designed to be consumed by ADS‑B alert/bot projects (e.g. Telegram alerts), personal dashboards, or analysis tools (Python, Excel, Grafana, etc.).

## EN — Available files (raw download)

Direct CSV links (useful for `curl/wget` or automated imports):

- Military (MIL): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-mil-images.csv
- Government (GOV): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-gov-images.csv
- Police / Law enforcement (POL): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-pol-images.csv
- Helicopter EMS / “Flying Doctors” (FD): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-flyingdocs.csv
- Civil (curated) (CIV): https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-civ-curated-images.csv

Tip: open a file on GitHub and click **Raw** to get the direct URL.

## EN — Possible use cases

- Real-time alerts: match aircraft seen by your ADS‑B receiver/feed (e.g. `aircraft.json`, Beast, SBS) against these lists; when HEX matches, send a notification (Telegram/Discord/email).
- Data enrichment: add registration, operator, type, links and images to “HEX-only” feeds.
- Filtering/classification: use `CMPG`, `Category` and `Tag1..Tag3` to build filters (e.g. only “Gov”, only “SAR”, only “VVIP”).
- Historical analysis: join your receiver logs/DB with these lists to build stats (by category/operator, etc.).
- Manual import: open CSV with Excel/LibreOffice or import into a database (SQLite/Postgres) to query it.

## EN — Quick examples

Download a list:

curl -L -o plane-alert-gov-images.csv
https://raw.githubusercontent.com/djrexishere91/df-adsb-lists/main/plane-alert-gov-images.csv

text

Filter by HEX:

grep -i "^06A3D5," plane-alert-gov-images.csv



Matching example (pseudo‑code):

seen_hex = stream_adsb_hex()
if seen_hex in csv_hex_list:
send_alert(seen_hex, metadata, img_url)



## EN — CSV format

All lists share the same header (same columns). Each row represents an aircraft identified by ICAO HEX (24‑bit).

Columns:
- HEX: ICAO 24-bit (e.g. `06A3D5`)
- Reg: registration (if known)
- Operator: operator/agency
- Type: aircraft model description (free text)
- ICAO Type: ICAO type designator (e.g. `B77L`, `A139`, etc.)
- CMPG: short group/category (e.g. Mil/Pol/Gov/Civ)
- Tag1 / Tag2 / Tag3: free tags (country, unit, callsign, notes, etc.)
- Category: free text category
- Link: reference URL (FlightRadar24, Airfleets, Wikipedia, etc.)
- Img1..Img4: image URLs (external sources)

Notes:
- Some fields may be empty.
- External links can change over time.

## EN — External links/images disclaimer

Images and external links belong to their respective owners and may be subject to separate terms of use.  
Broken links can happen over time.

## EN — License

See `LICENSE` (MIT).
