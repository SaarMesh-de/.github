# 🛰️ SaarMesh

Ein öffentliches [Meshtastic](https://meshtastic.org/) / [MeshCore](https://meshcore.co.uk/) Funknetz für die SaarLorLux-Region (Saarland, Lothringen, Luxemburg).

**🌍 Live-Karte:** [live.saarmesh.de](https://live.saarmesh.de) · **🏠 Projektseite:** [saarmesh.de](https://saarmesh.de)

---

## Über das Projekt

SaarMesh ist ein community-getragenes LoRa-Mesh-Netzwerk mit aktuell **800+ Nodes** in der Grenzregion Deutschland/Frankreich/Luxemburg. Das Netz nutzt Meshtastic- und MeshCore-kompatible Hardware und ermöglicht dezentrale, infrastrukturunabhängige Kommunikation über LoRa-Funk – nützlich für Funkamateure, Outdoor-Aktivitäten und als Backup-Kommunikationsmittel z.B. im Katastrophenschutz.

<!-- Screenshot: Live-Karte hier einfügen -->

## Netzwerk-Architektur

```
Meshtastic/MeshCore Nodes (800+)
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

Die Live-Karte läuft auf [CoreScope](https://github.com/Kpa-clawbot/CoreScope), einer Open-Source-Visualisierung für Meshtastic/MeshCore-Netzwerke. Wir tragen aktiv zu CoreScope bei (siehe unten).

## Mitmachen

Du bist im SaarLorLux-Raum und willst mitfunken?

1. Meshtastic- oder MeshCore-kompatible Hardware besorgen (z.B. Heltec, RAK, T-Beam)
2. Frequenzband/Kanalkonfiguration: <!-- TODO: Kanal-Infos ergänzen -->
3. In Reichweite eines bestehenden Nodes bringen – Abdeckung siehe [Live-Karte](https://live.saarmesh.de)
4. Fragen? <!-- TODO: Kontaktkanal (Telegram/Matrix/Discord?) -->

## Projekte & Beiträge

Diese Organisation bündelt Repos rund um SaarMesh und angrenzende Funk-/Homelab-Projekte:

| Repo | Beschreibung |
|---|---|
| [meshcore-chat](https://github.com/Saarlandpower/meshcore-chat) | Web-Chat-Interface für MeshCore (Flask + SocketIO) |
| [adsb-ha-proxy](https://github.com/Saarlandpower/adsb-ha-proxy) | Flask-Proxy für ADS-B-Flugdaten → Home Assistant |
| [ha-openligadb-team](https://github.com/Saarlandpower/ha-openligadb-team) | HA-Integration für Liga-Daten (1. FC Saarbrücken u.a.) |

**Upstream-Beiträge:** Wir arbeiten aktiv an [CoreScope](https://github.com/Kpa-clawbot/CoreScope) mit, u.a. Fixes für Versionsauflösung und Node-Staleness-Handling.

## Tech-Stack

- **Mesh:** Meshtastic, MeshCore, LoRa (868 MHz EU)
- **Visualisierung:** CoreScope
- **Infrastruktur:** VPS + Caddy (TLS), Raspberry Pi Gateways, Home Assistant
- **Zusatzdienste:** ADS-B/SDR-Integration, Wetter-/Warnkanäle über NINA

## Lizenz

<!-- TODO: Lizenz festlegen, z.B. MIT für eigene Repos -->

---

*Betrieben ehrenamtlich aus dem Saarland. Fragen, Feedback und Mitmacher willkommen.*
