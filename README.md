# Sukrut Nadigotti

Software engineer, CS @ Wayne State University. I build the software that runs warehouses — the whole stack, from the PLC program on the floor to the message broker that carries the orders.

## The material-handling stack

Five systems, five repos. One discipline holds them together: the supervisory layer can request, and the floor always keeps the last word.

| Layer | Repo | What it is | Demo |
|---|---|---|---|
| **The line** | [`fluxline`](https://github.com/SukrutN/fluxline) | A 3-way smart sorting line: an IEC 61131-3 Structured Text program for the OpenPLC runtime, its Python digital twin, and the seeded bench that proves the supervisory host's figures | [live](https://sukrutn.github.io/fluxline/) |
| **Integration** | [`switchyard`](https://github.com/SukrutN/switchyard) | A Go message broker: durable journaled lanes, KV state, a frozen wire protocol — and a linehost that speaks the sorting line over Modbus | [live](https://sukrutn.github.io/switchyard/) |
| **Slotting** | [`quay`](https://github.com/SukrutN/quay) | A forward-pick-face slotting engine: the kinship-reach score seats cartons by walk, weight, cube, and co-pick affinity — 10,000 cartons across 12,500 slots in one deterministic pass | [live](https://sukrutn.github.io/quay/) |
| **Picking & labor** | [`northspan`](https://github.com/SukrutN/northspan) | Pick-path planning (nearest neighbour + two-opt against the serpentine sweep) and engineered labor standards: minutes per unit, units per hour, a zone-by-band matrix | [live](https://sukrutn.github.io/northspan/) |
| **Fleet** | [`hearthlane`](https://github.com/SukrutN/hearthlane) | Multi-agent pathfinding for warehouse robots: CBS and ICBS over a painted floor, deadlines, congestion, and a release gate — a hundred robots planned jointly in about 67 ms | [live](https://sukrutn.github.io/hearthlane/) |

**Read them as one system:** [`manifest`](https://github.com/SukrutN/manifest) — the architecture that connects the five, one order's day through all of them, and the real-world interfaces each layer would meet ([live site](https://sukrutn.github.io/manifest/)).

## What to look at in any of them

Every repo holds its engine to its own site with characterization tests: the figures a page renders are locked, figure for figure, to the fixtures the engine publishes. A change that moves a number in one place fails the build everywhere. The engines are Java (quay, hearthlane), .NET (northspan), Go (switchyard), and Structured Text (fluxline); every one ships its own tests, its own CI gate, and its own workbench.

Outside the warehouse: [gather](https://github.com/SukrutN/gather) — a local-first novel-writing studio.

Site: [sukrutn.vercel.app](https://sukrutn.vercel.app/)
