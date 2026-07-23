# Website veröffentlichen — Anleitung

Die Site ist **statisch** (nur HTML/CSS/JS, keine Datenbank, kein Backend) und macht
**null externe Requests**. Dadurch ist Hosting trivial, schnell und DSGVO-einfach.

---

## 1. VORHER ausfüllen (Pflicht!)

Diese Platzhalter **müssen** vor dem Live-Gang ersetzt werden:

| Platzhalter | Wo | Was eintragen |
|---|---|---|
| `meine-kryptosteuer.de` | `index.html`, `impressum.html`, `datenschutz.html` (canonical + og:url + og:image), `robots.txt`, `sitemap.xml` | Deine echte Domain |
| `[HIER HOSTING-ANBIETER EINTRAGEN…]` | `datenschutz.html` Abschnitt 3 | z. B. „Netlify, Inc." / „Hetzner Online GmbH" |
| `[DATUM beim Veröffentlichen eintragen]` | `datenschutz.html` Abschnitt 7 | z. B. „Juli 2026" |
| USt-IdNr-Zeile | `impressum.html` | Eintragen **oder die Zeile löschen**, wenn du keine hast |

Schnell ersetzen (macOS):
```bash
cd website
grep -rl 'meine-kryptosteuer.de' . | xargs sed -i '' 's/DEINE-DOMAIN\.de/krypto-steuer.de/g'
```

> ⚠️ **Rechtlicher Hinweis:** Impressum und Datenschutzerklärung sind sorgfältige
> Standard-Vorlagen, **keine Rechtsberatung**. Für ein kommerzielles Produkt lohnt
> ein kurzer Check (Anwalt oder z. B. eRecht24) — besonders sobald du Geld nimmst.

---

## 2. Wo hosten? — Empfehlung

### 🥇 Empfehlung für deine Marke: **deutscher/EU-Hoster**
Deine ganze Positionierung ist „lokal, datenschutzfreundlich, deutsch". Dann ist es
konsequent, die Website auch in Deutschland zu hosten — das ist ein **Verkaufsargument**
und macht die Datenschutzerklärung wasserdicht.

| Anbieter | Kosten | Warum |
|---|---|---|
| **Netcup** (Webhosting) | ~2–4 €/Monat | Deutscher Hoster, sehr günstig, SSL inkl. |
| **All-Inkl** | ~5 €/Monat | Deutscher Klassiker, super Support, AVV einfach |
| **Uberspace** | ab 5 €/Monat | Deutsch, Entwickler-freundlich, „pay what you want" |
| **Hetzner** (Webhosting) | ~3 €/Monat | Deutscher Hoster, sehr solide |

**Vorgehen:** Paket buchen → Domain dazu → per **FTP/SFTP** den Inhalt des `website/`-Ordners
ins Web-Root (`/htdocs` bzw. `/public_html`) hochladen → fertig. SSL/HTTPS aktivieren
(bei allen per Klick, Let's Encrypt).

### 🥈 Schnellster Start (kostenlos, 5 Minuten): **Cloudflare Pages** oder **Netlify**
Wenn du erst mal *live* sein willst, ohne dich um Server zu kümmern:

**Netlify (am einfachsten):**
1. netlify.com → Account anlegen
2. „Add new site" → **„Deploy manually"** → den **Ordner `website/` einfach reinziehen**
3. Läuft sofort unter `xyz.netlify.app` (HTTPS automatisch)
4. Eigene Domain: „Domain settings" → Domain hinzufügen → DNS beim Registrar umstellen

**Cloudflare Pages:** analog, ebenfalls kostenlos, sehr schnelles CDN.

> Hinweis: Beides sind US-Unternehmen. Rechtlich okay (AVV abschließen, in der
> Datenschutzerklärung nennen), aber für deine „deutsch & datenschutzfreundlich"-Story
> ist ein DE-Hoster die sauberere Erzählung. **Mein Vorschlag: mit Netlify starten,
> bei ernsthaftem Launch auf einen deutschen Hoster umziehen.**

### Nicht empfohlen für dich: GitHub Pages
Ginge auch, bräuchte aber ein **öffentliches** Repo — dein App-Repo ist privat und
enthält Kopierschutz-Code. Dann lieber ein separates Repo nur für die Website.

---

## 3. Domain

- Registrar: **INWX**, **Netcup** oder **All-Inkl** (deutsch, ~5–15 €/Jahr für `.de`)
- Namensideen: `krypto-steuer.de`, `kryptosteuer-tool.de`, `deine-kryptosteuer.de`
- Prüfen: denic.de oder direkt beim Registrar

---

## 4. Nach dem Live-Gang (SEO-Startschuss)

1. **HTTPS prüfen** — muss überall greifen (auch `www` → non-`www` weiterleiten oder umgekehrt).
2. **Google Search Console** (search.google.com/search-console): Domain verifizieren →
   `sitemap.xml` einreichen. Das ist der wichtigste Schritt für die Indexierung.
3. **Bing Webmaster Tools** — dasselbe, kostet 2 Minuten, bringt Bing/ChatGPT-Suche.
4. **Social-Vorschau testen**: Link bei LinkedIn/X posten (oder LinkedIn Post Inspector) →
   das OG-Bild `assets/og-image.png` sollte erscheinen.
5. **Kein Cookie-Banner nötig!** Die Seite setzt keine Cookies und trackt nicht — das ist
   rechtlich sauber *und* ein Verkaufsargument. Bau **keinen** Banner ein, du bräuchtest ihn nicht.

---

## 5. SEO — was als Nächstes wirklich zieht

Technisch ist die Seite fertig optimiert (Titles, Meta-Description, Open Graph, Twitter Card,
JSON-LD mit `SoftwareApplication` + `Organization` + **`FAQPage`** für Rich Snippets,
saubere H-Hierarchie, `robots.txt`, `sitemap.xml`, keine externen Requests = top Ladezeit).

Was jetzt den Unterschied macht, ist **Inhalt**:

- **Schreib die Vergleichs-Story.** Genau der Fall, den wir dokumentiert haben:
  „Koinly zeigte 11.743 € steuerpflichtigen Gewinn — korrekt waren ~6.300 €."
  Das ist echter, belegbarer Content, der genau die Leute anzieht, die suchen.
- **Ziel-Suchbegriffe** (danach wird real gesucht):
  `Krypto Steuer Software`, `Solana Steuer`, `DeFi Steuer Deutschland`,
  `Krypto Steuer Steuerberater`, `§23 EStG Krypto`, `Staking Steuer Freigrenze`,
  `Krypto Futures Steuer Anlage KAP`
- **Ein Blog/Ratgeber-Bereich** (später) mit je einem Artikel pro Frage —
  z. B. „Wie versteuere ich Solana-Staking?", „Futures in der Anlage KAP".
  Jeder Artikel ist eine eigene Landeseite bei Google.
- **Backlinks**: In deutschen Krypto-Communities, Steuerberater-Netzwerken und
  Reddit (r/Finanzen, r/solana) dort auftauchen, wo genau diese Fragen gestellt werden.

---

## 6. Dateien

```
website/
├── index.html          One-Pager
├── impressum.html      Impressum (§5 DDG)
├── datenschutz.html    Datenschutzerklärung (DSGVO)
├── robots.txt          Suchmaschinen-Steuerung
├── sitemap.xml         Sitemap
└── assets/
    ├── site.css        Styles
    ├── site.js         Scroll-Reveal, Nav, FAQ
    ├── og-image.png    Social-Vorschaubild (1200×630)
    ├── quellen.png     Screenshot: Quellen
    ├── datenschutz.png Screenshot: Datenschutz-Tab
    └── report.png      Screenshot: Steuerberater-Report
```

**Lokal ansehen:** `open website/index.html` — oder mit Server:
`cd website && python3 -m http.server 8080` → http://localhost:8080
