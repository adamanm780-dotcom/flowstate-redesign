# FlowState — Website Redesign

Die neue Agentur-Website. Vanilla HTML/CSS/JS, kein Build-Step.
**Live-Vorschau:** https://flowstate-redesign.vercel.app
**Live-Domain:** https://yourflowstate.de — IONOS-Webspace, wird von
Vercel-Deploys NICHT aktualisiert (siehe Deploy)!

> Entwurfsstand: Preise (990 € / 1.890 €), „7 Tage", Adresse und Öffnungszeiten
> auf der Kontaktseite sind PLATZHALTER. Vor Go-Live ersetzen — siehe Liste unten.

## Struktur

```
index.html        Startseite (Hero mit 6 Parallax-Ebenen, Warum, Wiesbaden-Band,
                  Ablauf-Videos, Referenz-Tabs, Sonderangebot, Bewertungen,
                  Unterschied, KI, Team, FAQ, Finale)
projekte.html     Projektbühnen (Benjamin, Mehlhorn, CTA)
kontakt.html      Formular + Kontaktkarte + Karte (Consent) 
ansehen.html      Referenz-Viewer: Kundenseite im Frame + FlowState-Leiste
assets/
  style.css       komplettes Design-System (CI: Petrol #0B7C74, Amber #F2871C,
                  Encode Sans / Encode Sans Semi Condensed)
  app.js          Reveals, Wort-Split, Icon-Choreografien, Maus-Parallax,
                  Typewriter, Tabs, Slider, Popup, Karte, Formular-Schutz
  hero-p*.webp    Higgsfield-Ebenen (freigestellt) · hero-l5/6.svg Akzente
  schritt-*-v2.mp4  Ablauf-Videos (Freistellung fest eingebacken auf #F3F8F7 —
                  bei Umfärbung der Ablauf-Sektion neu rendern!)
  proj-*, bj-*    echte Screenshots der Kundenseiten
  kurhaus-night.webp  Kurhaus Wiesbaden (Holger Reinhardt, CC BY-SA 3.0)
```

## Lokal ansehen

Doppelklick auf `index.html` reicht. Sauberer: `npx serve -p 8766`

## Deploy — zwei getrennte Ziele!

**1. Vorschau (Vercel, Projekt „flowstate-redesign"):**

```
npx vercel --prod --yes
```

Einmalig pro Rechner vorher: `npx vercel link --yes --project flowstate-redesign`

**2. Live-Domain https://yourflowstate.de (separater Schritt):**
Die echte Domain hängt NICHT an Vercel. Sie wird vom IONOS-Webspace
ausgeliefert (Apache + `.htaccess`; `www` läuft zusätzlich über Cloudflare).
Ein Vercel-Deploy ändert an der Live-Domain also gar nichts — nach jeder
Änderung muss der komplette Stand (HTML-Dateien + `assets/` + `.htaccess`)
zusätzlich auf den IONOS-Webspace hochgeladen werden (FTP/IONOS-Zugang
liegt nicht im Repo, Upload wie gehabt vom PC aus).

„Live-verifiziert" gilt erst, wenn yourflowstate.de den neuen Stand zeigt.
Schnell-Check, welcher Stand wo liegt — die Cache-Version vergleichen:

```
curl -s https://yourflowstate.de/ | grep -o "style.css?v=[0-9]*"
curl -s https://flowstate-redesign.vercel.app/ | grep -o "style.css?v=[0-9]*"
```

## Zusammenarbeit (gleicher GitHub-Account, zwei Rechner)

1. Eigenen Commit-Namen setzen: `git config --global user.name "DeinVorname"`
2. Immer in dieser Reihenfolge hochladen:
   ```
   git add -A
   git commit -m "was du gemacht hast"
   git pull --rebase
   git push
   ```
3. `git pull --rebase` holt die Änderungen des anderen, ohne etwas zu überschreiben.

**Achtung Token:** Ein Fine-grained-Token, der nur auf `flowstate-website`
beschränkt ist, kann hier NICHT pushen — dieses Repo (`flowstate-redesign`)
in den Token-Berechtigungen ergänzen.

## Vor Go-Live ersetzen (Platzhalter)

- [ ] Echte Preise (Streichpreis muss real verlangt worden sein — UWG!)
- [ ] Bearbeitungsdauer („in 7 Tagen")
- [ ] Adresse + Öffnungszeiten (kontakt.html, 2× „Platzhalter"-Tag)
- [ ] Formular-Versand anschließen (FormSubmit o. ä.)
- [ ] Mehlhorn-Live-URL in `ansehen.html` (sites.mehlhorn.url) eintragen
- [ ] Team-Fotos statt Initialen
- [ ] Impressum/Datenschutz-Seiten verlinken (aktuell /impressum, /datenschutz)
- [ ] Entwurfs-Pill entfernen (`.draftpill` in allen HTML-Dateien)
- [ ] Referenz-Freigaben Benjamin + Mehlhorn dokumentieren

## Historie

Entstanden im Repo `flowstate-website`, Branch `redesign`, Ordner `entwurf/`
(dort liegt die komplette Entstehungsgeschichte inkl. Design-Spec unter
`docs/specs/2026-08-29-yourflowstate-redesign-design.md`).
