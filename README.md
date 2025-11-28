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
