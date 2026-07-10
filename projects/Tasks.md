---
tags: [tasks, shared]
status: active
updated: 2026-07-06
---

# Tasks — delt liste (menneske ↔ AI)

> Konvention: Dette er den delte opgaveflade. Agenter må appende
> daterede statuslinjer under en opgave, aldrig redigere eller slette
> menneskeskrevne linjer. Kanban.db er Hermes-intern (§5.7).

## Denne uge (før afrejse 13/7)
- [x] Onsdag 8/7: reboot-test hermes-vm (sudo reboot → verify egress-log: unit active, tabel live, nye loglinjer)
    - 2026-07-06 (claude): FULD PASS. Unit enabled+active, nftables-tabel/regel intakt, og frisk loglinje bekræftet post-reboot (15:40:15, SRC=172.17.0.2 DST=151.101.64.223:443). Hele kernel→rsyslog→fil-kæden verificeret efter genstart.
- [ ] Log-vækst tjek tirsdag + torsdag: ls -lh /var/log/hermes-egress.log
- [x] UniFi-regel 60→20 (10.60.60.20 → 10.20.20.30, TCP+UDP 22000)
    - 2026-07-06 (claude): Udført foran skema. Regel oprettet i UniFi (allow, auto-return), verificeret OPEN fra hermes-vm via /dev/tcp. VLAN 60 Internal-postur samtidig verificeret mod live config (Block All + scoped allows matcher docs).
- [ ] Torsdag 9/7: Kør read-node runbook (Syncthing på hermes-vm, receive-only, parring)
- [ ] Fredag 10/7: Verify read-node (sync komplet, Local Additions tom, Hermes kan læse Poland-noten)

## Rejse (DEADLINE 13/7)
- [ ] Book Liptov — 6 nætter (Tatralandia HV / Bešeňová / Mara Camping)
- [ ] Book Szczawnica — 1 nat (pensionat/spa, centralt)
- [ ] Book Kraków — 4 nætter (Kazimierz, aircon)
- [ ] Billeje: bekræft dækning Slovakiet + Tjekkiet
- [ ] E-vignetter: Slovakiet + Tjekkiet
- [ ] Autostol som checked equipment (gratis — bekræftet)

## Homelab (efter tur / august)
- [ ] OPS.md: GitHub-nøgleinventar (ctl-nøgle → kontoniveau 6/7, årsag til forsvinding ukendt) + omdøb misvisende nøglenavne på GitHub
- [ ] web_extract-backend beslutning (firecrawl/tavily/exa/parallel + evt. API-nøgle)
- [ ] Egress-log analyse: byg allowlist fra 2 ugers evidens (husk: 172.17.x er default bridge, ikke garanteret sandbox-only)
- [ ] Phase 8 firewall-tightening (ROADMAP §4 — add-specific-first, remove-blanket-last)
- [ ] VLAN 60-verifikation mod live UniFi (før posture-afhængige Hermes-faser)
    - 2026-07-06 (claude): Delvist lukket — Internal-retning verificeret (Block All + 8 scoped allows). AI→External (2 allows) udestår for fuld verifikation.
- [ ] Slet ~/Documents/workspace-OLD efter triage
- [ ] mDNS/AirPlay/printer-inventar før Phase 8 (household-flows der krydser VLANs)

## Hermes / AI (august)
- [ ] Git audit-log job (Docker VM, privat repo — OBS: bevidst data-egress-beslutning, ikke mekanik)
- [ ] Write-path fork afgøres: separat agents/hermes/-scoped mappe (foreløbigt lean) vs. flip node
- [ ] Agent-skriveadgang til vault (efter audit-job — Rev 3/4 trigger)
- [ ] OAuth-klient Google (Phase 1 prep — checkliste ligger klar)
- [ ] Session-protokol for agenter i vault (start: læs conventions; slut: log-linje om ændringer)
- [ ] Hermes dispatcher (Phase 1: single spawner, git-tracked schedule, cooldown-ladder)
- [ ] Phase 1 nftables-scope beslutning: dæk host-process egress, ikke kun sandbox-bridge
    - 2026-07-06 (claude): VLAN 60 er verificeret helt åben udadtil (UniFi Allow All). Egress-loggen (172.17.0.0/16) dækker KUN sandbox-trafik — hosts egen trafik (Hermes' LLM-kald, apt, Syncthing) er ulogget og uden UniFi-bagstopper. Overvej bredere nftables-scope eller separat host-egress-log når enforcement designes.