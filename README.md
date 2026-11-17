# RackNerd review: is a $21.99/year VPS enough, which plan should you pick, and what the promo price leaves out (full plan table, refunds, IPv6, port 25)

RackNerd is worth the money if you want a KVM virtual machine you fully control and you're comfortable in a terminal. It's a bad fit if you expect managed support, a money-back window, or an uptime guarantee that covers your VM. The entry point most people will look at is the 1 GB KVM special at **$21.99/year**, listed on RackNerd's own specials page; the 2 GB annual promo at **$35.99/year** is the plan that fits the widest range of real workloads.

Below: every plan I could confirm, the difference between the annual promo line and the standard monthly line (it's mostly CPU cores), the limits that only show up in low-end hosting forums, and the questions people actually ask before ordering.

> **Quick pick**
> - **Most readers:** 2 GB KVM annual promo, **$35.99/year**. Enough RAM for a LEMP stack, a VPN endpoint, a bot, or a handful of Docker containers.
> - **Cheapest box that still works:** 1 GB KVM annual promo, **$21.99/year**.
> - **Anything CPU-bound:** skip the promos and take the standard monthly 2 GB at **$20.59/month**, which ships with 3 vCores instead of 2.
> - **Don't want to touch a terminal:** cPanel shared hosting at **$5.59/month**.
>
> 👉 [Check the current annual KVM promo pricing](https://bit.ly/RacKnerd)

## RackNerd plans and prices

Two separate product lines get quoted interchangeably in reviews, and they are not the same thing. The annual promo line is what RackNerd advertises on its specials page; the standard line is billed monthly with more CPU per gigabyte of RAM. Prices below are as listed at the time of writing. Promos rotate, so confirm the number in the cart before you pay.

**Annual promo KVM (priced per year)**

| Plan | vCPU / RAM | SSD | Transfer | Price |
| --- | --- | --- | --- | --- |
| [ 1 GB KVM](https://bit.ly/RacKnerd) | 1 core / 1 GB | 20 GB | 3 TB | $21.99/year |
| [ 2 GB KVM](https://bit.ly/RacKnerd) | 2 cores / 2 GB | 35 GB | 5 TB | $35.99/year |
| [ 4 GB KVM](https://bit.ly/RacKnerd) | 3 cores / 4 GB | 60 GB | 7 TB | $59.99/year |
| [ 6 GB KVM](https://bit.ly/RacKnerd) | 6 cores / 6 GB | 100 GB | 12 TB | $89.99/year |
| [ 8 GB KVM](https://bit.ly/RacKnerd) | 7 cores / 8 GB | 150 GB | 20 TB | $119.99/year |

All of them include full root access, one dedicated IPv4, a 1 Gbps port, RAID-10 SSD storage, instant provisioning, and OS reinstalls from the control panel. Supported images include AlmaLinux, Rocky, CentOS, Fedora, Debian and Ubuntu; a custom ISO can be mounted through a support ticket.

**Standard monthly KVM (priced per month)**

| Plan | vCPU / RAM | SSD | Transfer | Price |
| --- | --- | --- | --- | --- |
| [ 512 MB](https://bit.ly/RacKnerd) | 1 core / 512 MB | 30 GB | 500 GB | $26.99/year |
| [ 1 GB](https://bit.ly/RacKnerd) | 2 cores / 1 GB | 50 GB | 1 TB | $17.99/month |
| [ 2 GB](https://bit.ly/RacKnerd) | 3 cores / 2 GB | 75 GB | 2 TB | $20.59/month |
| [ 4 GB](https://bit.ly/RacKnerd) | 4 cores / 4 GB | 130 GB | 3 TB | $24.59/month |
| [ 6 GB](https://bit.ly/RacKnerd) | 5 cores / 6 GB | 170 GB | 4 TB | $27.59/month |
| [ 8 GB](https://bit.ly/RacKnerd) | 6 cores / 8 GB | 220 GB | 5 TB | $36.59/month |
| [ 12 GB](https://bit.ly/RacKnerd) | 7 cores / 12 GB | 300 GB | 6 TB | $55.99/month |

The standard line also gives you more disk and more bandwidth per dollar of RAM, which is why the monthly 2 GB (75 GB SSD, 2 TB) looks oversized next to the annual promo 2 GB (35 GB SSD, 5 TB).

## What the promo price actually takes off you

It takes CPU cores, and the deeper the discount, the more of them.

The clearest case is seasonal: a $18.29/year 2 GB promo shipped with **1 vCore**, while the $20.59/month standard 2 GB ships with **3 vCores**. That's not a rounding difference. One core runs a static site, a WireGuard endpoint, a Discord bot, or a monitoring agent fine. One core does not enjoy compiling, running MySQL under load, or hosting three containers that each want a slice of CPU at the same time.

The standing annual promos are less aggressive but still leaner than the monthly line: the $35.99/year 2 GB lists 2 cores where the monthly 2 GB lists 3. Core counts also vary between promo batches for the same RAM tier, so read the spec line in the cart rather than trusting a table, including the ones above.

A rough line for deciding:

- **Personal blog, VPN, bot, uptime monitor, single small container:** the annual promo is the right buy. You're paying for RAM and disk, not compute.
- **Multiple containers, a small site with real traffic, a database that isn't idle, anything you compile on:** standard monthly 2 GB or the 4 GB annual promo.
- **A team, a CI runner, a game server with players:** standard monthly from 4 GB up.

👉 [Compare the standard monthly plans and their core counts](https://bit.ly/RacKnerd)

## Which plan for which job

Match the workload, not the spec sheet:

- **Static site, reverse proxy, DNS, Tailscale exit node:** 1 GB annual. $21.99/year covers it, and you'll be limited by the network long before the CPU.
- **WordPress or a small app with a database:** 2 GB annual, and put a cache in front of it. 35 GB of SSD is the real constraint here, not RAM.
- **Docker host with four or five small services:** 4 GB annual. 2 GB fills up faster than you expect once images and logs accumulate.
- **Self-hosted mail:** any tier works, and port 25 is **not blocked by default**, which is increasingly rare among cheap providers. Check with support that your chosen location allows outbound 25 before you migrate a domain.
- **Anything that needs Windows:** use the Windows VPS line with NVMe storage, from around $27.59/month for 2 GB. A $35.99/year KVM box will run a Windows ISO if you supply the license, but the CPU allocation is not sized for a desktop.
- **No terminal, just a website:** cPanel shared hosting at $5.59/month gets you 30 GB SSD, 2 TB monthly transfer, unlimited domains and databases, free SSL, LiteSpeed with LSCache, JetBackup daily off-site backups, Softaculous, KernelCare and free migration, deployed in Los Angeles, New York, Germany, France or Singapore. A $21.99/year VPS is cheaper on paper; the hours you'll spend assembling a web stack are not free.

## Who shouldn't buy RackNerd

- **You need a real uptime guarantee.** RackNerd's published SLA covers network transit and power with service credits, which is not the same as a guarantee that your VM stays up. If a five-nines commitment and a named account manager are requirements, this price tier is the wrong place to look.
- **You want managed hosting.** Every VPS here is unmanaged. Break your SSH config, misconfigure MariaDB, or need someone to tune PHP-FPM, and that's your job. RackNerd sells a fully managed add-on if you want it, but the base price doesn't include it.
- **You host user-generated content and can't handle takedowns.** RackNerd is a US company and responds to formal DMCA complaints, which can mean suspension while a dispute is resolved.
- **You're running high-traffic e-commerce.** Cheap and reliable enough for a small store, not the tier you want on a Black Friday spike.

## The limits that don't make the sales page

These come from long-term user reports rather than marketing material, and each one changes how you should use the box.

**Cancellation is unforgiving.** One user reported requesting cancellation, then missing a 24-hour confirmation window that landed on a public holiday; the data was wiped. RackNerd's position was that the customer initiated the cancellation and that the account couldn't be located. Whatever the merits, the practical lesson is the same: if you cancel, take your own backup first, and treat the confirmation step as urgent.

**DDoS protection is null-routing, not scrubbing.** Attacks get your IP routed to nowhere until the attack stops. One long-term customer's only real downtime in five years was exactly this, and support never emailed to say it had happened. You find out because your server stopped responding.

**cPanel storage rules are enforced by email.** A shared-hosting user reported repeated warnings over a few GB of image and asset zips being stored on the account, even as backups. Keep archives off the hosting account.

**IPv6 is not automatic.** Up to 100 free IPv6 addresses are available on request in the Los Angeles and France locations, via support ticket. Other locations don't have it yet, and one user reported being charged for address changes, so ask before you build around it.

**Shared hosting is the weak product.** The same user ran into images hosted on the cPanel account failing to load in Discord, spent days troubleshooting, and eventually closed the account, while describing the reseller/WHM side as working fine. If cPanel matters to you, start small.

**Promo codes often don't stack.** The promotional plan IDs are frequently excluded from coupon stacking. If a code fails at checkout, the plan is usually already discounted. Dedicated servers are the exception where a code does apply: `15OFFDEDI` is confirmed on RackNerd's own site for a lifetime discount, with dedicated servers starting at $139/month.

## Uptime, hardware and support

The honest summary is: support is better than the infrastructure.

Tickets come back fast. A long-term customer reports every ticket answered within 60 minutes, with support reading the community forum first and fixing rather than escalating. Reviewers have timed a 6-minute first response, and 10 to 20 minutes is a commonly cited range. An agent named Anthony Fye gets named repeatedly for solving problems outside the strict unmanaged scope: rDNS/PTR setup, MariaDB external connections, MX records, Ubuntu 24.04 upgrades. The founder, Dustin Cisneros, posts in public threads, including critical ones.

Uptime is decent but not spotless. The same long-term user's worst outage in years was the DDoS null-route. A different reviewer points at RackNerd's status page, which logs near-daily single-node incidents, reports micro-drops on a self-hosted VPN that didn't appear on competing VPSs, calls many of the IPs "burned," and argues the plans are oversold. Both accounts can be true at once: a $22/year box is fine for a homelab and a poor foundation for production. Hardware is sometimes older Xeon E5 v2 silicon, though newer Ryzen plans exist; check what a given location is running if single-thread performance matters.

## FAQ

**Does RackNerd offer refunds?**
No. RackNerd's own knowledge base states that per the terms of service, there is no refund and no money-back guarantee, and that includes immediate cancellation requests. Buy a small plan first if you're unsure.

**Will the renewal price jump?**
RackNerd markets its annual pricing as the recurring rate rather than a first-term teaser, and users report promo prices being honored across renewals. There's no contractual promise I can point to, so check the renewal line in the cart before paying rather than trusting any review, this one included.

**Can I install Windows?**
Yes, KVM is full virtualization and custom ISOs can be mounted by ticket, but you supply the license. For an actual Windows desktop or .NET environment, the Windows VPS line with NVMe starts around $27.59/month for 2 GB.

**Which datacenter should I pick from Asia or China?**
Los Angeles, specifically the DC-02 facility with the Asia-optimized route. Chinese Mobile users have reported reachability problems on some IP ranges, and RackNerd's own guidance is to choose a western US location and request a migration if the first IP performs badly. Twenty locations are available overall, spanning North America, Europe and Asia.

**Can I upgrade later?**
Yes, upgrades to the next tier are done from the control panel. Expect roughly a minute of downtime for the reboot.

**Are backups included?**
Not on VPS or dedicated servers. Shared and reseller plans include daily JetBackup snapshots stored off-site, described as best-effort; for a VPS, copy your data elsewhere on a schedule you control.

## Before you order

Decide by workload and the decision is simple. Blog, VPN, bot, monitor, or a single container: 1 GB annual promo at $21.99/year, and you're done. A stack with a database, or a handful of containers: 2 GB annual at $35.99/year. Anything CPU-bound or shared with other people: standard monthly, 2 GB at $20.59/month or the 4 GB annual promo. No terminal: cPanel shared at $5.59/month.

Two things to confirm on the order page, because both change weekly: whether the promo you want is still listed at that price, and whether your preferred location has stock. Los Angeles DC-02 in particular sells out during Black Friday, New Year and anniversary sales, which is when the deepest discounts appear.

👉 [Start with the 2 GB annual KVM promo and pick your datacenter](https://bit.ly/RacKnerd)
