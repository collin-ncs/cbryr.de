# cbryr.de

Meine persönliche Portfolio-Website. Hier zeige ich, wer ich bin, woran ich baue und was in meinem Homelab läuft.

🌐 **Live:** [cbryr.de](https://cbryr.de)

---

## Über die Seite

- **Eine einzige Seite**, ganz ohne Framework und ohne Build-Schritt: reines HTML, CSS und JavaScript
- **Hell- und Dunkelmodus**, folgt automatisch dem System und lässt sich umschalten
- **Funktioniert auf Handy und Desktop**
- **Schreibmaschinen-Effekt** für die Überschrift im Startbereich
- **Besucherzählung ohne Cookies** über [GoatCounter](https://www.goatcounter.com)
- **Eigene Konsole** unter [`/admin/`](https://cbryr.de/admin/), um Texte zu bearbeiten und Statistiken zu sehen

## Aufbau

```
.
├── index.html       # Die Website
├── content.json     # Alle Texte der Website
├── admin/
│   └── index.html   # Konsole zum Bearbeiten und für Statistiken
├── profil.jpg       # Profilfoto
├── robots.txt       # Hält Suchmaschinen von /admin/ fern
└── CNAME            # Eigene Domain für GitHub Pages
```

Die Texte stehen nicht direkt im HTML, sondern in `content.json`. Die Website lädt sie beim Aufruf. Falls die Datei einmal nicht lädt, werden die Texte angezeigt, die als Ersatz im HTML stehen.

## Texte bearbeiten

**Über die Konsole (empfohlen):**

1. [cbryr.de/admin/](https://cbryr.de/admin/) öffnen
2. Mit einem GitHub-Token anmelden (siehe unten)
3. Im Tab **Texte** ändern und auf **Veröffentlichen** klicken
4. Nach etwa einer Minute ist die Änderung online

**Direkt auf GitHub:** `content.json` öffnen, auf den Stift klicken, ändern und speichern. Wichtig: Texte immer in `content.json` ändern, nicht in `index.html`.

## Die Konsole

Die Konsole unter `/admin/` zeigt:

- ob die Website erreichbar ist und HTTPS aktiv ist
- den Status der letzten Veröffentlichung auf GitHub Pages
- Besucher pro Tag sowie Seiten, Herkunft, Länder, Browser, Systeme und Bildschirmgrößen der letzten 30 Tage
- die letzten Änderungen im Repository

Sie läuft komplett im Browser und spricht direkt mit der GitHub-API und der GoatCounter-API. Es gibt keinen eigenen Server.

### GitHub-Token für die Konsole

Ein **Fine-grained Personal Access Token** unter *Settings → Developer settings → Personal access tokens → Fine-grained tokens*:

| Einstellung | Wert |
|---|---|
| Repository access | Only select repositories → dieses Repo |
| Contents | Read and write |
| Pages | Read-only |
| Metadata | Read-only (automatisch) |

Der Token wird nur im eigenen Browser gespeichert, nie im Repository. Er kann ausschließlich dieses eine Repository ändern und lässt sich jederzeit widerrufen.

### Besucherzahlen

In der Konsole unter **Einstellungen** den GoatCounter-Code und einen API-Schlüssel mit dem Recht *Read statistics* eintragen.

## Hosting

- **Hosting:** GitHub Pages, veröffentlicht direkt aus dem `main`-Branch
- **Domain:** `cbryr.de`, DNS über Cloudflare (A- und AAAA-Einträge auf GitHub Pages, Proxy aus)
- **HTTPS:** Zertifikat von GitHub Pages

## Lokal ansehen

Weil die Texte per `fetch` aus `content.json` geladen werden, braucht es einen kleinen lokalen Webserver. Einfach die `index.html` per Doppelklick zu öffnen, zeigt nur die Ersatztexte.

```bash
python3 -m http.server 8000
```

Danach [http://localhost:8000](http://localhost:8000) im Browser öffnen.

---

Gebaut von Collin · [GitHub](https://github.com/collin-ncs) · [mail@cbryr.de](mailto:mail@cbryr.de)
