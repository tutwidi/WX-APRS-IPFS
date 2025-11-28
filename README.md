# WX-APRS-IPFS
https://ipfs.io/ipfs/QmbYnmaXNweUqshDtsc9bpU95GChc469zPYVH2jupc4JFy/

# YD9CVS Portable Station – WX → APRS → IPFS on Raspberry Pi 4B

This repository documents how I built a **portable weather station dashboard** that:

- collects **weather data** (local WX / APRS WX),
- processes and renders it with **WeeWX**,
- serves it over **IPFS** from a **Raspberry Pi 4B node**, and
- is fed by **Direwolf** listening to my **local VHF/UHF radio**.

The result is a fully static, censorship-resistant weather page like this:

> **Live example (snapshotted):**  
> `https://ipfs.io/ipfs/QmbYnmaXNweUqshDtsc9bpU95GChc469zPYVH2jupc4JFy/`

Station callsign: **YD9CVS**  
Platform: **Raspberry Pi 4B**  
TNC: **Direwolf** (software TNC)  
Network: **IPFS Kubo**

---

## 1. High-Level Architecture

```text
[Weather Sensors / APRS WX] 
          │
          │ RF (144.390 / local APRS freq)
          ▼
    [Radio + Audio Interface]
          │
          │ analog audio
          ▼
       [Direwolf]
   (APRS decoder on Pi)
          │
          │ decoded WX data (APRS frames, TCP/UDP, files)
          ▼
        [WeeWX]
 (Python weather engine)
          │
          │ HTML, graphs, JSON
          ▼
    [Static Web Output]
      /var/www/weewx
          │
          │ ipfs add -r
          ▼
     [IPFS Node on Pi]
 (Kubo daemon + pinning)
          │
          ├── Local gateway: http://raspi:8080/ipfs/<CID>/
          └── Public gateway: https://ipfs.io/ipfs/<CID>/
