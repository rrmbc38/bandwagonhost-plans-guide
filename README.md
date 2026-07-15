# VPS hosting for developers: finding a server that actually fits how you build — Docker, root SSH, IPv6, predictable bandwidth, price-per-GB and DC migration compared（附 BandwagonHost 全套餐选购清单）

If you've ever spent a Saturday night refreshing `/r/VPS` looking for a box that won't choke on a Docker build, you already know the genre. Every provider markets itself as "built for developers," then hands you a cPanel login and a 200ms routing detour through three peering disputes. So this piece is about *VPS hosting for developers* in the most literal sense — what a dev actually needs from a box, and where BandwagonHost (the KVM provider behind IT7 Networks, running since 2004) happens to fit into that picture.

We'll walk through the checklist a developer should apply to any VPS, then put BandwagonHost's full current catalog on the table — Standard KVM, CN2 GIA-E, Hong Kong / Tokyo / Osaka / Singapore CN2 GIA, and the 99.99% SLA E-Commerce line — so you can match a plan to your real workload instead of guessing.

## What developers actually need from a VPS (and what most reviews skip)

The "best VPS for developers" articles tend to rank providers by marketing copy. The actual developer checklist is shorter and blunter:

- **Full root over SSH** with tun/tap so PPP and VPN stacks work without a support ticket.
- **Real virtualization isolation** — KVM, not a shared container where a noisy neighbor's cron job eats your build minute.
- **A Linux catalog you control** — AlmaLinux, Rocky, Debian, Ubuntu, CentOS Stream, Fedora — plus a manual ISO install path for anything weird.
- **Predictable transfer, not "unlimited"** — metered plans tell you the real ceiling; unmetered "unlimited" usually means throttled at the edge.
- **IPv6 and rDNS from the panel** — because half the mail/relay breakage people post about is just missing PTR records.
- **Snapshots and free DC migration** — so you can test in Amsterdam and bail to Los Angeles when latency matters, without re-provisioning.
- **An API** — for the people who treat their fleet as code.

BandwagonHost ticks all of these because the whole platform runs on **KiwiVM**, an in-house control panel that is unapologetically functional: start/stop, OS reload, emergency console, rDNS, datacenter migration, snapshots, usage stats, and an API. No cPanel upsell, no WordPress baggage. The virtualization is KVM, so your CPU slice is yours. Every plan ships with a routed `/64` IPv6 subnet, a dedicated IPv4, and PPP/VPN (tun/tap) enabled out of the box — the three things shared-hosting refugees always email support about.

> "I want a nice VPS with Ubuntu, at least 512MB RAM, decent bandwidth and good uptime, that'll work with Ruby." — a request that surfaces in `/r/webdev` roughly once a week. BandwagonHost's entry $49.99/year plan covers all of it with change.

If you want to see the full inventory before reading further, 👉 [browse every BandwagonHost VPS plan and current stock](https://bwh81.net/aff.php?aff=79616&gid=1).

## The full BandwagonHost plan catalog, ranked by how a developer should read it

BandwagonHost's lineup is split into four families, and the price range is genuinely wide — from **$49.99/year** up to **$18,989.99/year**. The trick is knowing which family your workload belongs in before you start comparing rows.

**Standard KVM** — the budget tier. Enterprise RAID-10 SAS, E5 Xeons, 1 Gbps uplink, multiple US/EU/Canada/Amsterdam/Dubai locations, free migration between them. This is where dev environments, Linux learning boxes, personal sites, and CI runners live. No premium China routing, and that's fine for most non-China work.

**CN2 GIA-E (E-Commerce VPS)** — the middle tier. Premium China routing (CN2 GIA + CMIN2 + China Unicom Premium), access to 13+ datacenters including DC6/DC9 Los Angeles, Osaka Softbank, Netherlands 9929. This is the "I ship to users in mainland China and need it to actually load" tier. Annual billing here usually beats quarterly by a noticeable margin.

**Hong Kong / Tokyo / Osaka / Singapore CN2 GIA** — the latency tier. Equinix facilities, physically closest to mainland China, lowest round-trip. Priced accordingly. For VOIP, video conferencing, real-time APIs where 5ms vs 30ms is a revenue question.

**E-Commerce SLA Los Angeles** — the no-compromise tier. AMD EPYC, local NVMe RAID-10, 2.5–10 Gbps uplinks, dual redundant everything, **99.99% SLA**, SOC 1/2, ISO 27001, PCI DSS, HIPAA certifications. The choice when a production service has to stay up.

### Standard KVM VPS — the developer's daily driver

| Plan | RAM | CPU | Storage | Transfer | Pricing (lowest cycle shown) | Order |
|---|---|---|---|---|---|---|
| 20G KVM | 1 GB | 2 vCPU | 20 GB RAID-10 SSD | 1 TB/mo | $49.99/yr | [Order 20G KVM](https://bwh81.net/aff.php?aff=79616&pid=44) |
| 40G KVM | 2 GB | 3 vCPU | 40 GB RAID-10 SSD | 2 TB/mo | $52.99/half-yr · $99.99/yr | [Order 40G KVM](https://bwh81.net/aff.php?aff=79616&pid=45) |
| 80G KVM | 4 GB | 4 vCPU | 80 GB RAID-10 SSD | 3 TB/mo | $19.99/mo · $199.99/yr | [Order 80G KVM](https://bwh81.net/aff.php?aff=79616&pid=46) |
| 160G KVM | 8 GB | 5 vCPU | 160 GB RAID-10 SSD | 4 TB/mo | $39.99/mo · $399.99/yr | [Order 160G KVM](https://bwh81.net/aff.php?aff=79616&pid=47) |
| 320G KVM | 16 GB | 6 vCPU | 320 GB RAID-10 SSD | 5 TB/mo | $79.99/mo · $799.99/yr | [Order 320G KVM](https://bwh81.net/aff.php?aff=79616&pid=48) |
| 480G KVM | 24 GB | 7 vCPU | 480 GB RAID-10 SSD | 6 TB/mo | $119.99/mo · $1,199.99/yr | [Order 480G KVM](https://bwh81.net/aff.php?aff=79616&pid=49) |

Locations: Los Angeles (DC2/DC4/DC8), Fremont, New Jersey, New York, Vancouver, Amsterdam, Dubai, and others — all migratable between from the panel, free, no data loss.

For most developer workloads — a personal site, a side project, a Tailscale exit node, a Redis cache, a small Postgres, a CI runner — the **20G KVM at $49.99/year** is the cheapest box that meets the "real KVM, real root, real IPv6, real 99.9% uptime" bar. The **80G KVM** is the sweet spot when you start running Docker: 4 GB RAM is enough for a couple of containers plus the host, and the monthly billing option means you can spin it up for a sprint and cancel without committing a year.

### CN2 GIA-E (E-Commerce VPS) — premium routing for cross-Pacific workloads

| Plan | RAM | CPU | Storage | Transfer | Pricing (lowest cycle shown) | Order |
|---|---|---|---|---|---|---|
| CN2 GIA-E 20G | 1 GB | 2 vCPU | 20 GB SSD | 1 TB/mo | $49.99/qtr · $169.99/yr | [Order CN2 GIA-E 20G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 40G | 2 GB | 3 vCPU | 40 GB SSD | 2 TB/mo | $89.99/qtr · $299.99/yr | [Order CN2 GIA-E 40G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 80G | 4 GB | 4 vCPU | 80 GB SSD | 3 TB/mo | $56.99/mo · $549.99/yr | [Order CN2 GIA-E 80G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 160G | 8 GB | 6 vCPU | 160 GB SSD | 5 TB/mo | $86.99/mo · $879.99/yr | [Order CN2 GIA-E 160G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 320G | 16 GB | 8 vCPU | 320 GB SSD | 8 TB/mo | $159.99/mo · $1,599.99/yr | [Order CN2 GIA-E 320G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 640G | 32 GB | 10 vCPU | 640 GB SSD | 10 TB/mo | $289.99/mo · $2,759.99/yr | [Order CN2 GIA-E 640G](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 1.28TB | 64 GB | 12 vCPU | 1.28 TB SSD | 12 TB/mo | $549.99/mo · $5,499.99/yr | [Order CN2 GIA-E 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 1.28TB / 15TB | 64 GB | 12 vCPU | 1.28 TB SSD | 15 TB/mo | $679.00/mo · $6,790.00/yr | [Order CN2 GIA-E 15TB](https://bwh81.net/aff.php?aff=79616&gid=2) |
| CN2 GIA-E 1.28TB / 20TB | 64 GB | 12 vCPU | 1.28 TB SSD | 20 TB/mo | $899.00/mo · $8,999.00/yr | [Order CN2 GIA-E 20TB](https://bwh81.net/aff.php?aff=79616&gid=2) |

This is the line that made BandwagonHost's name in technical communities. The $169.99/year entry plan is the one most people who care about cross-Pacific stability end up on — quarterly billing works out to roughly $200/year, so annual is an instant ~$30 saving before any promo code. Access to DC6, DC9 (Los Angeles), Osaka Softbank, Netherlands 9929, and 13+ other migratable locations, all with CN2 GIA + CMIN2 + China Unicom Premium triple-network routing.

### E-Commerce SLA Los Angeles — production-grade, AMD EPYC + NVMe

| Plan | RAM | CPU | Storage | Transfer | Pricing (lowest cycle shown) | Order |
|---|---|---|---|---|---|---|
| E-Comm SLA 20G | 1 GB ECC | 2x AMD | 20 GB NVMe RAID-10 | 1 TB/mo | $65.89/qtr · $239.99/yr | [Order SLA 20G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 40G | 2 GB ECC | 3x AMD | 40 GB NVMe RAID-10 | 2 TB/mo | $116.99/qtr · $399.99/yr | [Order SLA 40G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 80G | 4 GB ECC | 4x AMD | 80 GB NVMe RAID-10 | 3 TB/mo | $69.99/mo · $699.99/yr | [Order SLA 80G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 160G | 8 GB ECC | 6x AMD | 160 GB NVMe RAID-10 | 5 TB/mo | $109.99/mo · $1,099.99/yr | [Order SLA 160G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 320G | 16 GB ECC | 8x AMD | 320 GB NVMe RAID-10 | 8 TB/mo | $199.99/mo · $1,999.99/yr | [Order SLA 320G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 640G | 32 GB ECC | 10x AMD | 640 GB NVMe RAID-10 | 10 TB/mo | $369.99/mo · $3,699.99/yr | [Order SLA 640G](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 1.28TB | 64 GB ECC | 12x AMD | 1.28 TB NVMe RAID-10 | 12 TB/mo | $699.99/mo · $6,999.99/yr | [Order SLA 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 1.28TB / 15TB | 64 GB ECC | 12x AMD | 1.28 TB NVMe RAID-10 | 15 TB/mo | $879.99/mo · $8,799.99/yr | [Order SLA 15TB](https://bwh81.net/aff.php?aff=79616&gid=3) |
| E-Comm SLA 1.28TB / 20TB | 64 GB ECC | 12x AMD | 1.28 TB NVMe RAID-10 | 20 TB/mo | $1,159.99/mo · $11,598.99/yr | [Order SLA 20TB](https://bwh81.net/aff.php?aff=79616&gid=3) |

This is the line where BandwagonHost stops pretending to be a budget provider. AMD EPYC dedicated cores, local NVMe RAID-10 (not SAS), 2.5–10 Gbps uplinks, dual redundant edge routers and core switches, dual diverse power feeds, dual NIC / dual diverse fiber to each node, and a 99.99% SLA backed by SOC 1 Type 2, SOC 2 Type 2, ISO 27001, NIST 800-53, PCI DSS and HIPAA certifications. Free IP change once every two weeks. Direct peering with Apple, Google, Facebook, Bytedance. If you're shipping a real product to real users in China and the rest of the world and uptime is a paycheck question, this is the tier.

### Hong Kong / Tokyo / Osaka / Singapore CN2 GIA — lowest latency to China

| Plan | RAM | CPU | Storage | Transfer | Location | Pricing (lowest cycle shown) | Order |
|---|---|---|---|---|---|---|---|
| HK 40G | 2 GB | 2 vCPU | 40 GB SSD | 500 GB/mo | Hong Kong (Equinix HK2) | $89.99/mo · $899.99/yr | [Order HK 40G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| HK 80G | 4 GB | 4 vCPU | 80 GB SSD | 1 TB/mo | Hong Kong (Equinix HK2) | $155.99/mo · $1,559.99/yr | [Order HK 80G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| HK 160G | 8 GB | 6 vCPU | 160 GB SSD | 2 TB/mo | Hong Kong (Equinix HK2) | $299.99/mo · $2,999.99/yr | [Order HK 160G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| HK 320G | 16 GB | 8 vCPU | 320 GB SSD | 4 TB/mo | Hong Kong (Equinix HK2) | $589.99/mo · $5,899.99/yr | [Order HK 320G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| HK 640G | 32 GB | 10 vCPU | 640 GB SSD | 6 TB/mo | Hong Kong (Equinix HK2) | $989.99/mo · $9,989.99/yr | [Order HK 640G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| HK 1.28TB | 64 GB | 12 vCPU | 1.28 TB SSD | 8 TB/mo | Hong Kong (Equinix HK2) | $1,889.99/mo · $18,989.99/yr | [Order HK 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 40G | 2 GB | 2 vCPU | 40 GB SSD | 500 GB/mo | Tokyo (Equinix TY8) | $89.99/mo · $899.99/yr | [Order Tokyo 40G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 80G | 4 GB | 4 vCPU | 80 GB SSD | 1 TB/mo | Tokyo (Equinix TY8) | $155.99/mo · $1,559.99/yr | [Order Tokyo 80G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 160G | 8 GB | 6 vCPU | 160 GB SSD | 2 TB/mo | Tokyo (Equinix TY8) | $299.99/mo · $2,999.99/yr | [Order Tokyo 160G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 320G | 16 GB | 8 vCPU | 320 GB SSD | 4 TB/mo | Tokyo (Equinix TY8) | $589.99/mo · $5,899.99/yr | [Order Tokyo 320G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 640G | 32 GB | 10 vCPU | 640 GB SSD | 6 TB/mo | Tokyo (Equinix TY8) | $989.99/mo · $9,989.99/yr | [Order Tokyo 640G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Tokyo 1.28TB | 64 GB | 12 vCPU | 1.28 TB SSD | 8 TB/mo | Tokyo (Equinix TY8) | $1,889.99/mo · $18,989.99/yr | [Order Tokyo 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 40G | 2 GB | 2 vCPU | 40 GB SSD | 500 GB/mo | Osaka (Equinix) | $49.99/mo · $499.99/yr | [Order Osaka 40G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 80G | 4 GB | 4 vCPU | 80 GB SSD | 1 TB/mo | Osaka (Equinix) | $86.99/mo · $869.99/yr | [Order Osaka 80G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 160G | 8 GB | 6 vCPU | 160 GB SSD | 2 TB/mo | Osaka (Equinix) | $165.99/mo · $1,665.99/yr | [Order Osaka 160G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 320G | 16 GB | 8 vCPU | 320 GB SSD | 4 TB/mo | Osaka (Equinix) | $329.99/mo · $3,199.00/yr | [Order Osaka 320G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 640G | 32 GB | 10 vCPU | 640 GB SSD | 6 TB/mo | Osaka (Equinix) | $549.99/mo · $5,549.99/yr | [Order Osaka 640G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Osaka 1.28TB | 64 GB | 12 vCPU | 1.28 TB SSD | 8 TB/mo | Osaka (Equinix) | $1,059.99/mo · $10,559.99/yr | [Order Osaka 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 40G | 2 GB | 2 vCPU | 40 GB SSD | 500 GB/mo | Singapore (Equinix SG1) | $49.99/mo · $499.99/yr | [Order SG 40G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 80G | 4 GB | 4 vCPU | 80 GB SSD | 1 TB/mo | Singapore (Equinix SG1) | $86.99/mo · $869.99/yr | [Order SG 80G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 160G | 8 GB | 6 vCPU | 160 GB SSD | 2 TB/mo | Singapore (Equinix SG1) | $165.99/mo · $1,665.99/yr | [Order SG 160G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 320G | 16 GB | 8 vCPU | 320 GB SSD | 4 TB/mo | Singapore (Equinix SG1) | $329.99/mo · $3,199.00/yr | [Order SG 320G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 640G | 32 GB | 10 vCPU | 640 GB SSD | 6 TB/mo | Singapore (Equinix SG1) | $549.99/mo · $5,549.99/yr | [Order SG 640G](https://bwh81.net/aff.php?aff=79616&gid=4) |
| Singapore 1.28TB | 64 GB | 12 vCPU | 1.28 TB SSD | 8 TB/mo | Singapore (Equinix SG1) | $1,059.99/mo · $10,559.99/yr | [Order SG 1.28TB](https://bwh81.net/aff.php?aff=79616&gid=4) |

These four locations are the answer to "I need 5ms, not 30ms, to my users." Equinix facilities throughout, direct routing via CN2 GIA (China Telecom), 9929 (China Unicom), and CMI (China Mobile). Osaka and Singapore are interesting outliers — they sit roughly halfway between Los Angeles GIA-E pricing and Hong Kong/Tokyo latency, so for Southeast Asian or Japan-focused dev work they're often the rational pick.

## Mapping developer workloads to the right tier

If the table above is too wide to reason about, here's how it actually breaks down in practice.

**Personal dev server, learning Linux, side project, Tailscale node** — the **20G KVM at $49.99/year** is the cheapest box that meets a developer's bar. 1 GB RAM is tight for Docker, but fine for a single Node/Go/Ruby process, a small Postgres, or a static site + Caddy reverse proxy.

**Docker host, small Kubernetes node, multi-service side project** — jump to **80G KVM** (4 GB RAM, $19.99/month or $199.99/year). Four GB is the practical floor for running the Docker daemon plus a couple of containers without swapping yourself to death.

**Production API serving users worldwide, including mainland China** — the **CN2 GIA-E 20G at $169.99/year** is where most serious users land. Premium routing, 13+ locations, and annual billing that beats quarterly by ~$30/year before any promo.

**Production service with an SLA obligation** — the **E-Commerce SLA 80G at $69.99/month or $699.99/year**. AMD EPYC, NVMe, 99.99% SLA, dual everything, compliance certifications. The first tier where you'd feel comfortable putting a paying customer's traffic on it.

**Real-time API for China users, latency-critical** — Hong Kong or Tokyo CN2 GIA, starting at $89.99/month. For VOIP, game servers, video conferencing bridges.

## The money-saving playbook for 2026

Promo codes for BandwagonHost have historically been recurring — meaning the discount applies to every renewal, not just the first invoice. The codes that circulated in 2025 (`BWHCGLUKKB`, `BWHNCXNVXV`) were retired late 2025. The `NODESEEK2026` code (6.77% recurring) was briefly live in February 2026 and has since expired. As of this writing there is **no verified active promo code** — so don't let a missing coupon stop you if you need a box today. New codes tend to drop around Double 11 (November), Black Friday, and New Year.

Even without a code, three things save real money:

1. **Go annual over quarterly.** On CN2 GIA-E, quarterly works out to ~$200/year vs $169.99 annual — that's $30/year automatic, no effort.
2. **Match the tier to your actual workload.** A personal dev server does not need $89.99/month Hong Kong CN2 GIA. The $49.99/year 20G KVM handles most "I want a Linux box on the internet" use cases.
3. **Use in-panel upgrades.** Outgrowing a plan? KiwiVM lets you upgrade by paying only the price difference, preserving your setup and any attached discounts. No re-provision, no migration headache.
4. **Watch for limited-edition "传家宝" (heirloom) plan restocks.** BandwagonHost periodically releases limited-stock plans — THE PLAN, MINICHICKEN, Box series — at prices that can be a third to a fifth of the equivalent regular plan. They sell out fast, but longtime users swear by them. Stock-monitoring tools exist in the community.

## The honest verdict on BandwagonHost as a developer VPS

It is not the right fit if you want cPanel, managed WordPress, or a 1-800 number to call about your Apache config. The self-managed model isn't a bug — it's the reason the pricing is what it is. BandwagonHost handles hardware, network, and infrastructure; you handle everything above the OS level.

It is the right fit if you're comfortable on a Linux command line (or willing to get comfortable), if you want real KVM isolation rather than container sharing, if you need IPv6 and rDNS from a panel instead of a ticket, if free DC migration matters to you, and if any part of your audience is in mainland China where CN2 GIA routing is the difference between a site that loads and a site that times out.

The word-of-mouth reputation in technical communities isn't accidental. The KiwiVM panel ships a feature set that matches what developers actually use, the hardware is owned outright (no reseller mystery when something breaks at 3 AM), and the pricing is transparent with no surprise renewal jumps. The entry tier is among the best $/year values in budget VPS, and the CN2 GIA-E line is what most cross-Pacific users should actually be looking at.

If you're ready to match a plan to your real workload, the full current inventory is here: 👉 [browse every BandwagonHost VPS plan and check live stock](https://bwh81.net/aff.php?aff=79616&gid=1). The 20G KVM at $49.99/year is the lowest-risk way to kick the tires, and upgrading in-panel later costs only the difference.
