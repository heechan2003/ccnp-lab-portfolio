# CCNP Labs

Lab exercises for CCNP ENCOR 350-401 and ENARSI 300-410, built on EVE-NG.

Each lab is built from a set of requirements, verified, then deliberately broken so the
faults have to be found from the symptoms.

## ENCOR 350-401

| Lab | Covers | Objectives |
|---|---|---|
| [Layer 2](labs/encor/layer2/) | VLANs, trunking, EtherChannel, STP/MST | 3.1.a–c |
| [IGP](labs/encor/igp/) | OSPFv2/v3, multiple areas, summarization, filtering | 3.2.a–b |
| [BGP](labs/encor/bgp/) | eBGP peering, best path selection, PBR | 3.2.c–d |

## ENARSI 300-410

Not started.

## Using these labs

Assumes a working EVE-NG install. Every lab folder holds a `.unl` — copy it to
`/opt/unetlab/labs/` on the EVE host, then:

```bash
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions
```

The lab then appears in the web UI. (The UI's own Import expects a `.zip`, so zip the
`.unl` first if you would rather go that route.)

**Images.** The `.unl` files reference these by exact filename:

| Node | Image in the `.unl` | What else works |
|---|---|---|
| Switches | `i86bi-linux-l2-adventerprisek9-15.1a.bin` | any IOL **L2** image, any version. An L3/router image will not — the Layer 2 lab needs switchports |
| Routers | `i86bi-linux-l3-jk9s-15.0.1.bin` | any IOL **L3** image. 15.0.1 predates OSPFv3 address-family syntax, so the IGP lab uses `ipv6 router ospf` |
| Test hosts | VPCS | ships with EVE-NG, nothing to obtain |

Cisco images are not distributed here. If your filename differs the topology still
imports — retarget the node image in the EVE UI and it boots.

**The `.unl` carries the topology only** — nodes, cabling and RAM, no device
configuration. Working the config out from the requirements is the exercise.

---

**Environment:** EVE-NG 6.2 on a home server — Cisco IOL L2/L3 (15.x) and CSR1000v
(IOS-XE 16.12) images, VPCS test hosts.
