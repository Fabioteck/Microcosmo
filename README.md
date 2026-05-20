# Microcosmo
Decentralized geospatial tracker for global sound systems culture, powered by Nostr Protocol and Lightning Network micro-payments.

# 🔊 Project Summary: Sound Systems Tracker

## 🎯 Vision & Philosophy (Data Sovereignty)
This project is an enterprise-ready, censorship-resistant geospatial platform designed to map the global sound systems culture and underground events. The core mission is to return absolute **Data Sovereignty** to creators and participants, filtering out traditional Web2 profiling and centralized corporate surveillance.

*   **100% Stateless & Cryptographic Identity:** No passwords, cookies, or tracking. Authentication relies strictly on asymmetric cryptographic keys (`npub`). 
*   **Zero-Trust Backend Validation:** The server does not trust the client. Every interaction (adding a node, updating coordinates) is packaged as a signed Nostr event. The backend validates the Schnorr signature (`sig`) against the user's public key (`pubkey`) before performing database mutations.
*   **Value-Gated Spatial Data:** The precise location of underground events (Geohash) is masked at the protocol level. It is unlocked via a programmable paywall using micro-transactions, protecting the privacy of the community while generating sustainable economic incentives.

---

## 🛠️ Hybrid Technological Stack

### Core Infrastructure
*   **Hardware:** Self-hosted production cluster running on Raspberry Pi 4 (Ubuntu Server CLI, Dockerized environments).
*   **Security & Gateway:** Protected via UFW, Fail2ban, SSL Let's Encrypt certificates, Apache Reverse Proxy, and globally scaled behind Cloudflare CDN.

### Protocol Layer (Nostr Integration)
*   **Relay Topology:** Private `nostr-rs-relay` acting as the master node, combined with a distributed multi-relay pool to eliminate Single Points of Failure (SPOF).
*   **Implemented NIPs:** 
    *   **NIP-52:** Ephemeral Geospatial/Geohash events for temporary map coordinates.
    *   **NIP-57 (Zaps):** Automated programmable paywalls using Bitcoin Lightning Network (LNURL/Sats) paired with traditional payment processors (Stripe/Fiat) for hybrid MVP validation.
    *   **NIP-04/44:** End-to-end encrypted P2P messaging channels for sound crews and ravers.
    *   **NIP-65:** Relay configuration and gossip hints.

### Application Layer
*   **Backend:** Laravel 11 engine utilizing a custom, modular *NostrCore* package, communicating with a PostgreSQL instance for high-throughput localized data routing.
*   **Frontend & Cross-Platform Mobile:** Vue.js 3 integrated with `nostr-tools` and modern browser cryptographic extensions (`window.nostr`). Wrapped via Capacitor for native, store-ready iOS/Android deployment.

