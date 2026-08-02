# coeff-web (web aplikace Coeff)

Statické stránky na GitHub Pages, doména `coeff.app` (soubor `CNAME`).
Struktura souborů je v README.md — tady je jen to, co se z kódu nepozná
a co už se jednou rozbilo.

Vlastník: Karel (hobby dev). Česky v komentářích i v komunikaci.
Appka samotná je vedle v repu `uefa_koeficient` (má vlastní CLAUDE.md).

## Nasazení

Push do `main` → GitHub Pages nasadí do minuty či dvou. Žádný build,
žádný generátor. Není kde nic zkompilovat, takže co je v repu, to je živé.

## Dvojjazyčnost — na tohle pozor

- `index.html` (cs) a `en.html` (en) jsou DVĚ ručně udržované stránky.
  Když se mění obsah, musí se změnit OBĚ; jinak se rozejdou.
  Výjimka schválená Karlem: odkaz na Strážce pramenů je jen na české
  stránce (Strážci jsou česky a pro ČR).
- `index.html` má v `<body>` skript, který **cizojazyčného návštěvníka
  přesměruje** na `en.html`. Detekce jde podle JAZYKA PROHLÍŽEČE
  (`navigator.language`), NE podle IP — VPN ani inkognito na tom nic
  nezmění (Karel to zkoušel přes Srbsko).
- Ruční volba má přednost a pamatuje se v `localStorage` pod klíčem
  `coeff-jazyk`. Odkaz „Česky" proto nese `?lang=cs`.
  **Zkušební adresa: `coeff.app/?lang=en`** — přehodí na angličtinu
  bez ohledu na prohlížeč.
- `hreflang` + `canonical` jsou na VŠECH čtyřech stránkách
  (index/en, soukromi/privacy), `x-default` = angličtina. Když přibude
  stránka, musí dostat pár taky — JS přesměrování na SEO nestačí.

## Keš stylů

Po každé změně `styles.css` je nutné zvednout `?v=DATUM` v `<link>`
v OBOU HTML. Bez toho se lidem s uloženou keší nový styl nenačte
a uvidí rozbité rozložení.

## Co se na web NEPÍŠE

- Nic, co by naznačovalo spojení s UEFA. V patičce je „Coeff není
  přidružený k UEFA" a to musí platit i o textech — proto se ani
  nepíše, že data bereme „přímo z UEFA".
- Žádné widgety a skripty třetích stran. Odkaz na X je prostý `<a>`
  s inline SVG (rozhodnuto 2026-07-31) — nechceme, aby web sledoval
  návštěvníky.

## Jak ověřovat změny

- **Preview pane u `file://` lže** — přesměrování neprovede věrně
  a adresu si resetuje na kořen. Pro test pusť lokální statický server
  a otevři `http://127.0.0.1:8099/`.
- Screenshoty pane občas zamrznou; spolehlivější je změřit prvek přímo
  v DOM (`getBoundingClientRect`) a zkontrolovat, že nikde nepřetéká.
- Vždy zkontrolovat i mobilní šířku (375 px), ne jen desktop — hlavička
  s vlajkou a odkazem na X se tam zalamuje jinak.
