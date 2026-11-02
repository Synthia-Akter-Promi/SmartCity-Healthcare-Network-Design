# SmartCity Healthcare Network Design

A Cisco Packet Tracer network-design project for a metropolitan healthcare system connecting six medical units: Main Hospital (MH), Diagnostic Center (DC), Emergency Response Unit (ERU), Research Institute (RI), Pharmacy Hub (PH), and Remote Health Clinic (RHC).

## Project Overview

The proposed network supports communication among hospitals, clinics, research facilities, pharmacies, and emergency services. The Main Hospital is designed as the central backbone. The topology includes interconnected routers and switches, departmental end devices, and network services.

## Network Scale

| Medical unit | Required devices |
|---|---:|
| Main Hospital (MH) | 300 |
| Diagnostic Center (DC) | 150 |
| Research Institute (RI) | 120 |
| Pharmacy Hub (PH) | 100 |
| Emergency Response Unit (ERU) | 80 |
| Remote Health Clinic (RHC) | 60 |
| **Total** | **810** |

## Architecture and Services

- Each medical unit is represented by a router.
- MH acts as the central network backbone and has direct links to RI and ERU.
- DC, PH, and RHC are interconnected through a switch connected to MH, as specified in the brief.
- ERU has a second connection to RI for redundancy.
- Each unit is intended to have its own email server (for example, `mail.mh.local` and `mail.ri.local`).
- MH is intended to host DNS and the web service `www.smartcityhealth.local`.

## Addressing and Routing Requirements

- The base network is generated from the group's student-ID rule in the assignment brief; the actual base network depends on the group's ID-derived value.
- VLSM is required to allocate subnets for the six units according to host requirements.
- Static-routing exercises include next-hop, exit-interface, recursive, and floating static routes.
- RIPv2 is required among RI, PH, DC, and ERU; MH participates in both static and RIPv2 routing.
- The design requires traffic to reroute through ERU if the MH–RI link fails.
- RHC's intended primary path is via PH using RIPv2, with a backup floating static route via ERU.
- PH's required fallback is a recursive static route via RI.

## DHCP Requirements

- DC and ERU: router-based DHCP.
- PH and RHC: dedicated DHCP servers.
- MH and RI: static IP addressing for all devices.

## Project File

**Cisco Packet Tracer simulation:** [SmartCity_Healthcare_Network.pkt](./SmartCity_Healthcare_Network.pkt)

Download the `.pkt` file from the repository and open it with Cisco Packet Tracer.

## Repository Contents

```text
SmartCity-Healthcare-Network-Design/
├── README.md
├── SmartCity_Healthcare_Network.pkt
└── Documentation/
    └── IMPLEMENTATION_NOTES.md
```

Additional topology diagrams, the original assignment brief, and evidence screenshots can be added as they are uploaded.

## Validation Checklist

Before describing the project as fully implemented, verify these items in Packet Tracer and add screenshots or command outputs:

- [ ] Confirm router and switch interface addressing against the IP addressing table.
- [ ] Verify VLSM subnet sizes and default gateways for all six units.
- [ ] Verify DHCP leases in DC, ERU, PH, and RHC.
- [ ] Verify static routes and RIPv2 route learning (`show ip route`, `show ip protocols`).
- [ ] Disconnect the MH–RI link and verify traffic reroutes through ERU.
- [ ] Verify RHC's primary route via PH and backup route via ERU.
- [ ] Verify PH's recursive static fallback via RI.
- [ ] Verify DNS resolution and HTTP access to `www.smartcityhealth.local`.
- [ ] Verify email delivery between MH and RI.

## Tools

- Cisco Packet Tracer
- IPv4 addressing and VLSM
- Static routing and RIPv2
- DHCP, DNS, HTTP, and email services

## Author

**Synthia Akter Promi**  
[GitHub Profile](https://github.com/Synthia-Akter-Promi)

## Disclaimer

This is an educational network simulation. Do not use real patient information or connect this lab directly to a production healthcare network.
