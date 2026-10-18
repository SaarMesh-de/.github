# 🛰️ SaarMesh

Ein öffentliches [MeshCore](https://meshcore.co.uk/) Funknetz für die SaarLorLux-Region (Saarland, Lothringen, Luxemburg).

**🌍 Live-Karte:** [live.saarmesh.de](https://live.saarmesh.de) · **🧰 Werkzeuge:** [live.saarmesh.de/werkzeuge](https://live.saarmesh.de/werkzeuge/) · **🏠 Projektseite:** [saarmesh.de](https://saarmesh.de) · **💬 Forum:** [forum.saarmesh.de](https://forum.saarmesh.de) · **☕ Unterstützen:** [ko-fi.com/saarmesh](https://ko-fi.com/saarmesh)

---

## Über das Projekt

SaarMesh ist ein community-getragenes LoRa-Mesh-Netzwerk mit aktuell **1200+ Nodes** (davon rund 1000 Repeater) in der Grenzregion Deutschland/Frankreich/Luxemburg. Das Netz nutzt MeshCore-kompatible Hardware und ermöglicht dezentrale, infrastrukturunabhängige Kommunikation über LoRa-Funk – nützlich für Funkamateure, Outdoor-Aktivitäten und als Backup-Kommunikationsmittel z.B. im Katastrophenschutz.

![CoreScope Live-Karte](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/corescope-live-map.png)
*Live-Ansicht der Mesh-Aktivität auf [live.saarmesh.de](https://live.saarmesh.de)*

## Netzwerk-Architektur

```
MeshCore Nodes (1200+)
        │  LoRa 868 MHz
        ▼
  Observer (21, Repeater/Companions an Raspberry Pis u.a.)
        │  MQTT (TLS, Auth)
        ▼
  EMQX-Broker ──► CoreScope (live.saarmesh.de)
        │                  │
        │                  ├─ Spam-Monitor, Repeater-Relevanz, Positions-Check,
        │                  │  Statistik, Tropo-Vorhersage
        ▼                  ▼
  SaarMesh-Bot (Mesh + Telegram)      VPS (bold-wright, Caddy/TLS)
```

Die Live-Karte läuft auf [CoreScope](https://github.com/Kpa-clawbot/CoreScope), einer Open-Source-Visualisierung für MeshCore-Netzwerke. Wir tragen aktiv zu CoreScope bei (siehe unten).

## Werkzeuge rund ums Netz

Neben der Live-Karte betreiben wir eine Reihe eigener Auswertungen – alle gesammelt unter **[live.saarmesh.de/werkzeuge](https://live.saarmesh.de/werkzeuge/)**:

| Werkzeug | Was es macht |
| --- | --- |
| 🗺️ [Live-Karte](https://live.saarmesh.de) | Nodes, Pakete, Pfade und Kanäle in Echtzeit (CoreScope, 90 Tage Historie) |
| 🛡️ [Spam-Monitor](https://live.saarmesh.de/spam/) | Erkennt Flut-Absender, auffälligen Traffic und Funkstörungen |
| 📡 [Repeater-Relevanz](https://live.saarmesh.de/relevanz/) | Welche Repeater tragen das Netz? Inklusive Ausfall-Simulation für mehrere Repeater gleichzeitig |
| 📍 [Positions-Check](https://live.saarmesh.de/positionen/) | Nodes, deren eingetragene Position nicht zu ihren Funkpartnern passt |
| 📊 [Statistik](https://live.saarmesh.de/statistik/) | Nachrichten, Adverts, aktive Nodes, Netzwachstum, Kanäle und Serverzustand |
| 🌫️ [Tropo-Vorhersage](https://live.saarmesh.de/tropo/) | Überreichweiten durch Inversionen, kalibriert an echten SaarMesh-Empfängen |

## Projekte & Beiträge

Unsere Repos liegen unter dem Account [**@SaarMesh-Bot**](https://github.com/SaarMesh-Bot):

| Repo | Beschreibung |
| --- | --- |
| [meshcore-webapp](https://github.com/SaarMesh-Bot/meshcore-webapp) | **Meshcore Webapp by SaarMesh.de** – Browser-App für MeshCore-Companions per USB, Bluetooth oder TCP/WiFi: Live-Traffic mit Pfaden und SNR, Chat, Karte mit Nachbar-Linien, Repeater-Verwaltung, Telemetrie, Trace-Route, automatisch entdeckte Kanäle und Regionen. Eine HTML-Datei, installierbar als App. **[▶ Direkt öffnen](https://saarmesh-bot.github.io/meshcore-webapp/)** |
| [Meshcore-bot-for-Home-Assistant](https://github.com/SaarMesh-Bot/Meshcore-bot-for-Home-Assistant) | SaarMesh-Fork der HA-Add-ons von [vipje](https://github.com/vipje/Meshcore-bot-for-Home-Assistant) (Bot mit 80+ Befehlen + Proxy für ein gemeinsam genutztes Funkmodul) – mit **DE-Paket**: DWD-/NINA-Warnungen, Pegelstände und Hochwasseralarm, Feiertage, deutsche Standardwerte, DX-Jagd |
| [meshcore-chat](https://github.com/SaarMesh-Bot/meshcore-chat) | Web-Chat-Interface für MeshCore (Flask + SocketIO) |
| [meshcore-channels](https://github.com/SaarMesh-Bot/meshcore-channels) | Fork des community-gepflegten [Kanal-Katalogs](https://github.com/marcelverdult/meshcore-channels) – wir haben dort die im Funkverkehr verifizierten SaarLorLux-/DE-/FR-/LU-Hashtag-Kanäle eingebracht |
| [CoreScope (Fork)](https://github.com/SaarMesh-Bot/CoreScope) | Arbeits-Fork für unsere Upstream-Beiträge zu CoreScope |

### Upstream-Mitarbeit an CoreScope

Der Betrieb eines Netzes dieser Größe (aktuell **1200+ Nodes, 21 Observer**) fördert regelmäßig Randfälle zutage, die in kleineren Meshes nicht auffallen — und die wir als Fixes zurück an das Projekt geben. Bisher sind **8 unserer Pull Requests in CoreScope gemergt**:
**[github.com/Kpa-clawbot/CoreScope/pulls?q=author:SaarMesh-Bot](https://github.com/Kpa-clawbot/CoreScope/pulls?q=is%3Apr+author%3ASaarMesh-Bot)**

Inhaltliche Schwerpunkte:

- **Kanäle & Region-Scopes** — Nachträgliches Auflösen bisher unbekannter Kanal-/Scope-Pakete, sobald neue Schlüssel bekannt werden (#2133), und Kanalfilter auch für live per WebSocket eintreffende Pakete (#2192).
- **Relay-Attribution & Neighbor-Graph** — korrekte Dekodierung von ANON_REQ-Absendern (#1866) sowie Vorschläge für einen konfigurierbaren Vertrauens-Schwellwert (`pathTrust`) gegen falsche Kanten aus kurzen Hash-Präfixen.
- **Ingestor- & Server-Robustheit** — Schema-Erkennung schlägt laut fehl statt still einen falschen DB-Modus zu cachen (#1909), Behebung eines stillen Datenverlusts beim `last_seen`-Update von Relays (#1855), Entkopplung des Watchdog-Loggings von blockierender I/O (#1853) und keine teuren Pro-Beobachtung-Abfragen mehr im Hot-Path (#1829).
- **Frontend & Darstellung** — Korrekturen an der RX-Coverage-Ansicht (#1860).

Ältere Beiträge (Versionsauflösung, Node-Staleness) stammen aus der Frühphase des Projekts unter dem Account [@Saarlandpower](https://github.com/Saarlandpower).

## Mitmachen

Du bist im SaarLorLux-Raum und willst mitfunken?

1. MeshCore-kompatible Hardware besorgen (z.B. Heltec, RAK, T-Beam, XIAO) – Einstieg Schritt für Schritt: [saarmesh.de/einsteiger](https://saarmesh.de/einsteiger)
2. Frequenzband: **868 MHz (EU)**. Region-Scope: **saarlorlux** (Standard für das Saarland – Details siehe [saarmesh.de/regions](https://saarmesh.de/regions))
3. In Reichweite eines bestehenden Nodes bringen – Abdeckung siehe [Live-Karte](https://live.saarmesh.de)
4. Fragen oder Kontakt: Kanal **#saarland** im Mesh, im [Forum](https://forum.saarmesh.de) oder über [Telegram](https://saarmesh.de) (Link auf der Projektseite)

## SaarMesh-Bot

Der SaarMesh-Bot hängt direkt am Mesh und spiegelt in die Telegram-Gruppe:

- **Wetter & Warnungen** — Wetterabfrage (auch per PLZ), DWD-/NINA-Warnungen kompakt und dedupliziert im Kanal **#warnings**
- **Region-Scopes** — sendet pro Kanal im passenden Scope (z.B. #saarland → saarlorlux), Antworten übernehmen den Scope der Anfrage
- **Forum-Feed** — neue Themen aus Ankündigungen und Stammtisch landen im Mesh (#saarland) und auf Telegram
- **ADS-B-Status**, Einsteiger-Hinweise und mehr

![SaarMesh-Bot Dashboard](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/saarmesh-bot-dashboard.png)
*Internes Dashboard des SaarMesh-Bots zur Kanal-Steuerung und Nachrichtenübersicht.*

![saarmesh.de](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/saarmesh-homepage.png)
*Die Projektseite [saarmesh.de](https://saarmesh.de) mit Dokumentation, Regions-Struktur und Live-Feed aus dem #saarland-Kanal.*

## Tech-Stack

- **Mesh:** MeshCore, LoRa (868 MHz EU), Region-Scopes (saarlorlux, de-sl, de-rp, de-west …)
- **Visualisierung:** CoreScope (Go-Engine) + eigene Auswertungen
- **Infrastruktur:** VPS + Caddy (TLS), EMQX-MQTT-Broker, Raspberry-Pi-Observer und -Gateways
- **Clients:** Meshcore Webapp (Browser/PWA), Home-Assistant-Add-ons

## Lizenz

Die Projekte in dieser Organisation stehen, sofern nicht anders angegeben, unter der [MIT-Lizenz](https://opensource.org/licenses/MIT).

---

*Betrieben ehrenamtlich aus dem Saarland. Fragen, Feedback und Mitmacher willkommen.*

Wenn du das Projekt unterstützen möchtest (Hardware, Serverkosten): [☕ ko-fi.com/saarmesh](https://ko-fi.com/saarmesh)
