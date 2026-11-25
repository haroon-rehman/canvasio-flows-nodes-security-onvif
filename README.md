# ONVIF NG

Canvas IO Workflows — maintained integration/fork of an independent Node-RED node package.

## Canvas IO

| | |
|--|--|
| Domain | Security / ONVIF |
| Development status | Integrated in local harness (canvasio-flows-dev) |
| Palette category (operational) | `Canvas IO` |
| Config nodes | remain `category: "config"` |
| Local repository | `canvasio-flows-nodes/canvasio-flows-node-security-onvif` |
| npm package name | `@canvasio/node-security-onvif` (`0.9.0-canvasio.1`); upstream `node-red-contrib-onvif-ng` `0.9.0` |

`canvasio-flows-nodes` is an organizational parent only — not a monorepo. One node package = one Git repository.

This repository is a **Canvas IO-maintained integration/fork**. Protocol and node runtime logic originate from upstream; Canvas IO changes are limited to integration, presentation, and local development packaging.

## Nodes

### Operational (palette: Canvas IO)

- `onvif-device`, `onvif-discovery`, `onvif-events`, `onvif-imaging`, `onvif-media-profile`, `onvif-media-stream`, `onvif-recording`

### Configuration

- `onvif-config`

## Development

```powershell
cd C:\GitHub\canvasio\canvasio-flows\canvasio-flows-nodes\canvasio-flows-node-security-onvif
npm install
```

Local harness:

```powershell
cd C:\GitHub\canvasio\canvasio-flows\canvasio-flows-dev
npm install
cd C:\GitHub\canvasio\canvasio-flows\canvasio-flows-core
node packages/node_modules/node-red/red.js --userDir C:\GitHub\canvasio\canvasio-flows\canvasio-flows-dev
```

Open http://localhost:1880

## Testing

No automated unit tests.

## Upstream

| | |
|--|--|
| Original package | `node-red-contrib-onvif-ng` |
| Upstream project | https://github.com/panthercomputers/node-red-contrib-onvif-ng |

Canvas IO does not claim authorship of the original upstream implementation.

## License

Apache-2.0 — see ``LICENSE``.

---

## Upstream documentation

The following sections retain useful upstream technical documentation (adapted only where needed).

# node-red-contrib-onvif-ng

[![npm version](https://img.shields.io/npm/v/node-red-contrib-onvif-ng.svg)](https://www.npmjs.com/package/node-red-contrib-onvif-ng)
[![Node-RED](https://img.shields.io/badge/Node--RED-compatible-red)](https://flows.nodered.org/node/node-red-contrib-onvif-ng)
[![Security Policy](https://img.shields.io/badge/security-policy-brightgreen)](./SECURITY.md)


Modernized ONVIF nodes for Node-RED 4.x using the agsh/onvif library (ONVIF 4.7 compatible).

This project is a **maintained continuation** of  
**node-red-contrib-onvif-nodes** by Bart Butenaers, updated for modern Node-RED runtimes and real-world camera behavior.

## Legacy branch

The `bart-original` branch preserves the original upstream implementation by Bart Butenaers.
It is retained for historical reference and is not merged into `main`.
Archived screenshots and legacy documentation are preserved for reference but are not part of the current API contract.
---

## âœ¨ Key Features

- âœ… Node-RED 4.x compatible
- âœ… ONVIF 4.7 tested
- âœ… Centralized profile cache (no repeated device queries)
- âœ… Reliable media stream handling
- âœ… Explicit capability discovery nodes
- âœ… Clear status reporting
- âŒ PTZ intentionally excluded (for now)

---

## ðŸ“¦ Included Nodes

### Configuration
- **onvif-config**  
  Handles device connection, authentication, profile caching, and connection health.

---

### Media
- **onvif-media-stream**  
  - Get Stream URI  
  - Get Snapshot URI  
  - Reconnect  

  Uses cached profiles only â€” no live negotiation at runtime.

- **onvif-media-profile**  
  - Get profiles  
  - Create / delete profiles  
  (Profile tokens come from the device profile cache.)

---

### Discovery / Capability Inspection

These nodes are **discovery tools**, not continuous event streams.

- **onvif-events**  
  Discovers supported ONVIF Events and topics via `GetEventProperties`.

- **onvif-recording**  
  Discovers recording capabilities and configuration.

> â„¹ï¸ These nodes intentionally return similar payloads for each invocation.
> Their purpose is **capability inspection**, not live subscriptions.

---

## ðŸš« PTZ Status

PTZ support is **not included** in this release.

Reason:
- Not used in production by the maintainers
- High UI and device-specific complexity
- Better handled as a future optional module

PTZ work done so far has been intentionally carved out and may return in a later release or as a community contribution.

---

## ðŸ” Profile Cache Contract (Important)

- Profiles are fetched **once** during device initialization
- Cached centrally in `onvif-config`
- All nodes consume profiles from the cache
- No node performs live profile discovery during runtime

This ensures:
- Predictable behavior
- Faster execution
- No UI deployment deadlocks

---

## ðŸ“¡ Supported Cameras

Tested with:
- Hanwha / Wisenet cameras
- Other ONVIF-compliant devices (results may vary)

ONVIF implementations vary widely â€” this project favors **robust behavior over strict spec assumptions**.

---

## ðŸ“œ License

Apache License 2.0

Original work:
- Â© 2018 Bart Butenaers

Modernization and maintenance:
- Â© 2025â€“2026 Panther Computers

---

## ðŸ¤ Contributing

Issues and PRs are welcome.

Please:
- Target the `main` branch
- Keep changes aligned with Node-RED 4.x
- Avoid device-specific hacks unless clearly isolated

---

## ðŸ§­ Project Status

Active maintenance  
PTZ deferred  
Stability prioritized

## Maintainer

Maintained by **Panther Computers**.

The maintainer is also an employee of  
[Mobile Surveillance Solutions](https://www.mobilesurvsolutions.com),  
where ONVIF-based systems are used in production environments.


