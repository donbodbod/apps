# Validation record

## Public package 0.1.1 — verified 2026-11-24

| Check | Result |
| --- | --- |
| Official Olares CLI chart lint | PASS |
| Official Olares CLI chart package | PASS |
| Market import and installation | PASS |
| Upgrade from 0.1.0 to 0.1.1 | PASS |
| Private gateway browser access | PASS: SABnzbd 5.1.3 setup wizard and queue |
| Hostname integration | PASS: injected entrance hostname accepted |
| Default download directories | PASS: /downloads/incomplete and /downloads/complete |
| Initial article cache | PASS: 256 MB |
| Provider connection | PASS: Eweka SSL 563, strict certificate validation, 50 connections, 20 articles per request |
| Complete download to local storage | PASS: 35.91 GB in 273 seconds; SABnzbd reported 125.4 MiB/s, approximately 1.05 Gbit/s |
| Idle resident memory | Approximately 139 MB after transfer; peak use not measured |
| Public screenshots | Actual setup and empty queue; no provider credentials or personal job names |
| Icon | 256x256 PNG hosted with the package assets |
| Market artwork metadata | Featured image and two gallery screenshots declared with immutable published asset URLs; the same artwork was visually verified in Market on the private 0.1.3 profile |

The transfer was a download-only test. It does not validate repair or unpacking performance, sustained disk throughput or the provider's maximum account speed. The byte total is the sum of NZB article segment sizes; SABnzbd displays approximately 33.4 GiB.

## Integration correction

Version 0.1.0 installed but SABnzbd rejected browser requests arriving through the Olares proxy as external access. Version 0.1.1 initializes proxied browser access once, behind the private Olares authentication gateway. API key protection and hostname validation remain enabled. A bootstrap marker preserves subsequent user configuration choices.

## Separate NAS profile — verified 2026-11-25

A private 0.1.2 profile was tested with existing NAS shares. The application remained reachable after the upgrade, configuration was retained, six categories and their paths persisted after page reload, and SABnzbd successfully wrote a backup archive to each of two mounted shares. Temporary downloads remained on local Olares storage.

This is additional integration evidence for a separately configured profile. The public 0.1.1 chart in this directory declares local download storage; it does not include that installation's NAS mounts, credentials, categories or history.

## Remaining validation

- Run repair and unpacking on a suitable test job.
- Measure peak memory during download and post-processing.
- Run a dedicated restart/recovery test with a queued or interrupted job.
- Validate the public chart on arm64 hardware; amd64 is the tested installation.

Chart checks validate packaging, not application performance. No upstream Market submission or CI success is implied by these local checks.
