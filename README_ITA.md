# 🔊 Riassunto del Progetto: Sound Systems Tracker

## 🎯 Vision & Filosofia (Sovranità dei Dati)
Questo progetto è una piattaforma geospaziale di livello enterprise, censorship-resistant e decentralizzata, progettata per mappare la cultura dei sound system e degli eventi underground globali. La missione principale è restituire la totale **Sovranità dei Dati** ai creatori e ai partecipanti, eliminando la profilazione Web2 e la sorveglianza delle corporazioni centralizzate.

*   **Identità Crittografica Stateless al 100%:** Niente password, cookie o tracciamenti. L'autenticazione si basa esclusivamente su coppie di chiavi crittografiche asimmetriche (`npub`).
*   **Validazione Backend Zero-Trust:** Il server non si fida del client. Ogni interazione (aggiungere un punto, aggiornare le coordinate) viene impacchettata come un evento Nostr firmato digitalmente. Il backend valida la firma Schnorr (`sig`) contro la chiave pubblica (`pubkey`) dell'utente prima di effettuare qualsiasi modifica al database.
*   **Dati Spaziali Protetti da Paywall:** La posizione precisa degli eventi underground (Geohash) è mascherata a livello di protocollo. Viene sbloccata tramite un paywall programmabile che sfrutta le micro-transazioni, proteggendo la privacy della comunità e generando al contempo un modello economico sostenibile.

---

## 🛠️ Stack Tecnologico Ibrido

### Infrastruttura Core
*   **Hardware:** Cluster di produzione auto-ospitato su Raspberry Pi 4 (Ubuntu Server CLI, ambienti Dockerizzati).
*   **Sicurezza & Gateway:** Protetto tramite UFW, Fail2ban, certificati SSL Let's Encrypt, Reverse Proxy Apache e scalato globalmente dietro CDN Cloudflare.

### Layer di Protocollo (Integrazione Nostr)
*   **Topologia Relay:** Server privato `nostr-rs-relay` come nodo principale, combinato con un pool multi-relay distribuito per eliminare qualsiasi Single Point of Failure (SPOF).
*   **NIP Implementati:** 
    *   **NIP-52:** Eventi geospaziali/geohash effimeri per le coordinate temporanee sulla mappa.
    *   **NIP-57 (Zaps):** Paywall automatici e programmabili tramite Bitcoin Lightning Network (LNURL/Sats) accoppiati a processori tradizionali (Stripe/Fiat) per la validazione flessibile dell'MVP.
    *   **NIP-04/44:** Canali di messaggistica P2P crittografati end-to-end per crew e raver.
    *   **NIP-65:** Configurazione dei relay e indicazioni di propagazione.

### Layer Applicativo
*   **Backend:** Engine Laravel 11 basato su un pacchetto modulare custom *NostrCore*, interfacciato con un'istanza PostgreSQL per la gestione e il routing dei dati locali ad alte prestazioni.
*   **Frontend & Mobile Cross-Platform:** Vue.js 3 integrato con `nostr-tools` e con le estensioni crittografiche del browser (`window.nostr`). Pacchettizzato tramite Capacitor per un deployment nativo su store iOS/Android.
