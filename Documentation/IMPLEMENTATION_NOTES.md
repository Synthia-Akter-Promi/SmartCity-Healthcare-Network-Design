# Implementation Notes and Verification

This document separates requirements in the supplied assignment brief from implementation evidence that still needs to be checked in the Packet Tracer file.

## Requirements from the project brief

1. Six units: MH (300 devices), DC (150), RI (120), PH (100), ERU (80), and RHC (60).
2. MH is the backbone; MH connects directly to RI and ERU. DC, PH, and RHC connect through a switch to MH. ERU also connects to RI.
3. Each unit has an email server. MH hosts DNS and the web server `www.smartcityhealth.local`.
4. DHCP: DC and ERU use router DHCP; PH and RHC use dedicated DHCP servers; MH and RI use static addressing.
5. VLSM is required. The base network must be calculated from the student-ID rule in the assignment brief.
6. Static routes: MH→DC next-hop; ERU→MH exit-interface; PH→DC recursive via RI; RHC→MH floating static via ERU.
7. RIPv2 is required on RI, PH, DC, and ERU; MH participates in static and RIPv2 routing.
8. On MH–RI failure, traffic should reroute through ERU. RHC should prefer PH and use ERU as backup.

## Evidence to add

For a strong portfolio repository, add screenshots or command output for:

- `show ip interface brief` on each router.
- `show ip route` and `show ip protocols` on routing devices.
- DHCP client leases in each DHCP-enabled unit.
- Successful ping tests between representative subnets.
- DNS lookup and browser access to `www.smartcityhealth.local`.
- Email test between MH and RI.
- A before/after test showing failover when the MH–RI link is disconnected.

## Important

The topology diagram and project brief are supplied source files. This notes file does not claim that every listed requirement has been configured successfully. Update the checklist in `README.md` only after testing the `.pkt` file.
