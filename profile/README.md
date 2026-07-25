# 🛰️ SaarMesh

Ein öffentliches [MeshCore](https://meshcore.co.uk/) Funknetz für die SaarLorLux-Region (Saarland, Lothringen, Luxemburg).

**🌍 Live-Karte:** [live.saarmesh.de](https://live.saarmesh.de) · **🏠 Projektseite:** [saarmesh.de](https://saarmesh.de) · **☕ Unterstützen:** [ko-fi.com/saarmesh](https://ko-fi.com/saarmesh)

---

## Über das Projekt

SaarMesh ist ein community-getragenes LoRa-Mesh-Netzwerk mit aktuell **1000+ Nodes** in der Grenzregion Deutschland/Frankreich/Luxemburg. Das Netz nutzt MeshCore-kompatible Hardware und ermöglicht dezentrale, infrastrukturunabhängige Kommunikation über LoRa-Funk – nützlich für Funkamateure, Outdoor-Aktivitäten und als Backup-Kommunikationsmittel z.B. im Katastrophenschutz.

![CoreScope Live-Karte](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/corescope-live-map.png)
*Live-Ansicht der Mesh-Aktivität auf [live.saarmesh.de](https://live.saarmesh.de)*

## Netzwerk-Architektur

```
MeshCore Nodes (1000+)
        │  LoRa
        ▼
   Gateway-Nodes
        │
        ▼
  CoreScope (live.saarmesh.de)
        │  Caddy Reverse Proxy (TLS)
        ▼
   VPS (bold-wright)
```

Die Live-Karte läuft auf [CoreScope](https://github.com/Kpa-clawbot/CoreScope), einer Open-Source-Visualisierung für MeshCore-Netzwerke. Wir tragen aktiv zu CoreScope bei (siehe unten).

## Projektseite

![saarmesh.de](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/saarmesh-homepage.png)
*Die Projektseite [saarmesh.de](https://saarmesh.de) mit Dokumentation, Regions-Struktur und Live-Feed aus dem #saarland-Kanal.*

## Mitmachen

Du bist im SaarLorLux-Raum und willst mitfunken?

1. MeshCore-kompatible Hardware besorgen (z.B. Heltec, RAK, T-Beam)
2. Frequenzband: **868 MHz (EU)**. Region-Scope: **saarlorlux** (Standard für das Saarland – Details siehe [saarmesh.de/regions](https://saarmesh.de/regions))
3. In Reichweite eines bestehenden Nodes bringen – Abdeckung siehe [Live-Karte](https://live.saarmesh.de)
4. Fragen oder Kontakt: Kanal **#saarland** im Mesh, oder über [Telegram](https://saarmesh.de) (Link auf der Projektseite)

## Projekte & Beiträge

Diese Organisation bündelt Repos rund um SaarMesh und MeshCore:

| Repo | Beschreibung |
| --- | --- |
| [meshcore-chat](https://github.com/SaarMesh-Bot/meshcore-chat) | Web-Chat-Interface für MeshCore (Flask + SocketIO) |

### Upstream-Mitarbeit an CoreScope

Unsere Live-Karte läuft auf [CoreScope](https://github.com/Kpa-clawbot/CoreScope). Der Betrieb eines Netzes dieser Größe (aktuell **1000+ Nodes**, 18 Observer) fördert regelmäßig Randfälle zutage, die in kleineren Meshes nicht auffallen — und die wir als Fixes zurück an das Projekt geben.

Unsere Beiträge laufen über den Account [**@SaarMesh-Bot**](https://github.com/SaarMesh-Bot). Aktueller Stand aller eingereichten Pull Requests:
**[github.com/Kpa-clawbot/CoreScope/pulls?q=author:SaarMesh-Bot](https://github.com/Kpa-clawbot/CoreScope/pulls?q=is%3Apr+author%3ASaarMesh-Bot)**

Inhaltliche Schwerpunkte:

- **Relay-Attribution & Neighbor-Graph** — korrekte Zuordnung von Repeatern bei Uhren-Abweichung, ANON_REQ-Kanten im Nachbarschaftsgraphen, und ein konfigurierbarer Vertrauens-Schwellwert (`pathTrust`), der bei großen Netzen falsche Kanten aus kurzen Hash-Präfixen verhindert.
- **Ingestor-Robustheit** — Behebung eines stillen Datenverlusts beim `last_seen`-Update von Relays (seit einem Read-only-Refactor wirkungslos), Entkopplung des Watchdog-Loggings von blockierender I/O, und Vermeidung teurer Pro-Beobachtung-Abfragen im Hot-Path.
- **Frontend & Darstellung** — kleinere Korrekturen an der RX-Coverage-Ansicht.

> **Status:** Die meisten dieser PRs sind eingereicht und review-fertig, warten aber am GitHub-Actions-Freigabe-Gate für externe Contributor auf Aktivierung ihrer CI-Läufe. Der Stand oben aktualisiert sich automatisch.

Ältere Beiträge (Versionsauflösung, Node-Staleness) stammen aus der Frühphase des Projekts unter dem Account [@Saarlandpower](https://github.com/Saarlandpower).

## Tech-Stack

- **Mesh:** MeshCore, LoRa (868 MHz EU)
- **Visualisierung:** CoreScope
- **Infrastruktur:** VPS + Caddy (TLS), Raspberry Pi Gateways
- **Bot-Features:** Wetterabfrage, NINA-Warnkanal, ADS-B-Status im Mesh

![SaarMesh-Bot Dashboard](https://raw.githubusercontent.com/SaarMesh-de/.github/main/assets/saarmesh-bot-dashboard.png)
*Internes Dashboard des SaarMesh-Bots zur Kanal-Steuerung und Nachrichtenübersicht.*

## Lizenz

Die Projekte in dieser Organisation stehen, sofern nicht anders angegeben, unter der [MIT-Lizenz](https://opensource.org/licenses/MIT).

---

*Betrieben ehrenamtlich aus dem Saarland. Fragen, Feedback und Mitmacher willkommen.*

Wenn du das Projekt unterstützen möchtest (Hardware, Serverkosten): [☕ ko-fi.com/saarmesh](https://ko-fi.com/saarmesh)
