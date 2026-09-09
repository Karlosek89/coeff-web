# coeff.app

Web aplikace **Coeff** — evropské fotbalové koeficienty
(https://github.com/Karlosek89/uefa_koeficient).

Statické stránky na GitHub Pages, doména `coeff.app` (soubor `CNAME`).

- `index.html` — hlavní stránka (česky)
- `en.html` — hlavní stránka (anglicky)
- `soukromi.html` / `privacy.html` — zásady ochrany osobních údajů (cs/en),
  URL pro Google Play listing
- `styles.css` — společný vzhled („pohárová noc" jako v aplikaci)

## Generované stránky (needitovat ručně)

- `zebricek/` (cs) a `ranking/` (en) — hlavní tabulka zemí a stránka
  každé z 55 zemí. **Vyrábí je `tool/generuj_web.dart` v repu appky
  `uefa_koeficient`** ze stejných dat a stejného výpočtu jako aplikace;
  ruční úprava se přepíše při dalším běhu. Blok v `sitemap.xml` mezi
  značkami `GENEROVANO` patří k nim.
- Spuštění z repa appky: `dart run tool/generuj_web.dart ../coeff-web`,
  pak commit a push tady. Cíl: běžet automaticky po nočním importu
  výsledků (napojení na cron appky).
