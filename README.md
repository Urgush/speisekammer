# 🥫 Speisekammer

Eine private Lagerverwaltung für Küche und Vorräte – als einzelne HTML-Datei, läuft direkt im Browser, kein eigener Server nötig.

**Live-Demo:** [urgush.github.io/speisekammer](https://urgush.github.io/speisekammer)

---

## Was kann die App?

- 📷 **Barcode scannen** mit der Handykamera (ZXing)
- 🔍 **Produktdaten automatisch abrufen** über [OpenFoodFacts](https://world.openfoodfacts.org)
- 📦 **Ein- und Ausbuchen** von Vorräten mit Mengenangabe
- ✏️ **Manuelle Erfassung ohne Barcode** für Frischware wie Obst und Gemüse
- 🏷️ **Kategorien, Behälter und Einheiten** frei konfigurierbar, Behälter per Drag & Drop sortierbar
- 📅 **MHD-Tracking** mit automatischer Status-Anzeige (OK / bald ablaufend / abgelaufen)
- 🔎 **Filter & Suche** nach Name, Kategorie, Behälter und Notizen
- 🔐 **Login per E-Mail/Passwort** (Google & Apple Login vorbereitet)
- ☁️ **Echtzeit-Sync** zwischen mehreren Geräten über Supabase
- 📊 **Excel-Export** (kompatibel mit LibreOffice Calc), optional nur gefilterte Ansicht
- 🎲 **KI-Rezeptvorschläge** – generiert einen Prompt zum Einfügen in Claude, ChatGPT & Co.
- 🧪 **Entwicklermodus** mit Sync-Diagnose für Fehlersuche

## Verwendete Technik

| Bereich | Technologie |
|---|---|
| Barcode-Scanning | [ZXing](https://github.com/zxing-js/library) |
| Produktdatenbank | [OpenFoodFacts API](https://world.openfoodfacts.org/data) |
| Auth & Datenbank | [Supabase](https://supabase.com) (PostgreSQL, Row Level Security, Realtime) |
| Excel Export/Import | [SheetJS](https://sheetjs.com/) |
| Drag & Drop Sortierung | [SortableJS](https://sortablejs.github.io/Sortable/) |
| Hosting | GitHub Pages |

Die App ist ein reines Frontend – Supabase übernimmt Authentifizierung, Datenhaltung und Echtzeit-Synchronisation, GitHub Pages liefert nur die statische HTML-Datei aus.

## Selbst hosten

1. Repository forken oder `index.html` herunterladen
2. Eigenes [Supabase](https://supabase.com)-Projekt erstellen (kostenloses Tier reicht aus)
3. In Supabase die Tabellen `inventory` und `user_settings` mit Row Level Security anlegen (SQL-Skript siehe `SETUP.md`, folgt)
4. Supabase Project-URL und `anon public` Key im Code eintragen (`SUPABASE_URL`, `SUPABASE_ANON_KEY`)
5. In Supabase unter **Authentication → URL Configuration** die eigene Hosting-URL als Site URL und Redirect URL eintragen
6. Über GitHub Pages oder einen beliebigen Webserver hosten

## Datenhaltung & Sicherheit

Jeder Nutzer meldet sich über Supabase Auth an (E-Mail/Passwort, Google und Apple folgen). Die Daten liegen in einer PostgreSQL-Datenbank bei Supabase, abgesichert über Row Level Security – jeder Nutzer kann ausschließlich seine eigenen Daten lesen und schreiben. Änderungen werden per Supabase Realtime sofort auf alle angemeldeten Geräte übertragen.

## Lizenz

Dieses Projekt steht unter der [GNU General Public License v3.0](LICENSE). Du darfst es frei nutzen, verändern und weitergeben – Änderungen müssen ebenfalls unter der GPL v3 veröffentlicht werden.

## Mitwirken

Issues und Pull Requests sind willkommen. Dies ist ein privates Hobbyprojekt ohne Garantie auf Support oder Weiterentwicklung in bestimmtem Tempo.

## Hinweis zur Entstehung

Diese App wurde im Dialog mit [Claude](https://claude.ai) (Anthropic) entwickelt – von der ersten Idee über Architekturentscheidungen bis zur laufenden Fehlersuche. Sämtlicher Code wurde iterativ per "Vibe Coding" erstellt: in natürlicher Sprache beschrieben, generiert, getestet und verfeinert.
