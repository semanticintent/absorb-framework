# A historical lens: electricity, the dotcom era and AI

Version 0.1 (draft), 2026-10-30. This is an **interpretive note**, not part of the testable framework in `SPEC.md`. It uses two earlier technology waves to ask where in a delivery system the opportunity and the friction tend to sit. Historical analogies are easy to fit after the fact, so each claim below is marked as sourced or interpretation.

## The pattern

In both earlier waves the capability arrived first and the organization changed later. Early adopters replaced the old part with the new one and kept the old design around it, and gains were small. The gains came when work was redesigned around the new capability, and the people who understood a specific constraint did better than the people who merely had the technology.

This is the same claim ABSORB makes: faster development is not faster delivery until the surrounding system changes.

## Wave 1: electricity

**Sourced.**
- Factories first replaced the steam engine with one large electric dynamo and kept the central shafts and belts. This "group drive" layout kept the old shafting in place, and gains were small. The "unit drive" put a motor on each machine, which removed the overhead shafting, allowed lighter single-story factories and gave more flexibility in layout (David 1990).
- Learning to design unit-drive factories took time, because it developed through decentralized experience across many firms. Only about half of US factory mechanical drive was electrified by the early 1920s, roughly four decades after the first central power station (David 1990).
- A history-news interview with David describes the redesign as needing more worker training and new contracts, because workers made more decisions, and points to World War I labor-supply changes as a spur (Paul David interview).
- Electrical fire risk produced institutions. Underwriters Laboratories was founded in Chicago in 1894 by William Henry Merrill, with funding from local insurance groups. The first National Electrical Code was published in 1897. Insurers were involved: one group of mutual insurers reported electrical fires in 23 of 65 New England mills it insured, and five incompatible codes existed by 1896 (UL history; NEC history).

**Interpretation, mapped to ABSORB.**

| Electricity | ABSORB dimension | Link |
| --- | --- | --- |
| Motor swapped, layout kept | D1 Flow and constraints | Code gets faster inside a delivery process designed for slow code |
| Redesigning the floor around flow | D1, D5 | Stage mapping and constraint-first sequencing |
| Codes and testing set up after fires, pushed by insurers | D3 Risk-tiered governance | Governance tends to arrive after early incidents, and the party bearing the loss often drives it |
| Training and new contracts | D8 People and change | Roles and decision rights change with the work |
| Decentralized learning across firms | D7 Measurement | Shared baselines and published cases speed learning |

## Wave 2: the dotcom era

**Sourced.**
- The Nasdaq Composite peaked at 5,048.62 on 10 March 2000 and fell by more than 75 percent by October 2002 (International Banker).
- Webvan built its warehouses and fulfillment from scratch (a reported $1 billion order with Bechtel) and expanded into many cities before proving its first market. It shut down in June 2001 and filed for bankruptcy in July 2001. Peapod, which used existing supermarket infrastructure, survived (Wikipedia, Webvan).
- PayPal's early fraud problem nearly sank it. The article cites a fraud rate above 120 basis points in the early 2000s and, according to *The PayPal Wars*, losses of $2,300 an hour. Max Levchin built an anomaly-detection system called Igor, and fraud fell within months of the fixes (Plaid, "PayPal's history of fighting fraud"). The article gives no date for Igor.
- The Sarbanes-Oxley Act was signed on 30 July 2002 in response to accounting scandals including Enron, Tyco, Adelphia, Peregrine Systems and WorldCom (Wikipedia). These were corporate accounting failures, not strictly internet failures, so the link to the dotcom era is loose.
- PCI DSS 1.0 was released in December 2004, prompted by online shopping and rising card fraud. The article cites North American online merchants losing about 3.6 percent of sales to stolen or fraudulent cards in 2000 (Secureframe).

**Interpretation, mapped to ABSORB.**

| Dotcom era | ABSORB dimension | Link | Evidence |
| --- | --- | --- | --- |
| Webvan: fulfillment built too fast | D1 Flow and constraints | Online ordering is fast only if the physical stage can absorb it | Sourced |
| PayPal and fraud | D2 Verification and evidence | Trust and verification, not features, decided who survived | Sourced for PayPal. Generalizing to the whole era is interpretation |
| SOX and PCI DSS after the bust | D3 Risk-tiered governance | Standards followed incidents | Dates sourced, link interpretive |
| Sites without a clear way to earn | D4 Intent and specification | Cheap building exposes unclear intent | Interpretation, not checked here |
| Load failures, later hosting industry | D5 Environment and platform | Platform fit for volume | Interpretation, not checked here |
| Unclear ownership of "the web" | D6 Accountability and ownership | Ownership sat between IT, marketing and new roles | Interpretation, not checked here |
| Traffic as the measure of success | D7 Measurement | Goodhart's law in practice | Interpretation, not checked here |
| New roles, then layoffs | D8 People and change | Roles shift and then contract | Interpretation, not checked here |

## Wave 3: AI (the working hypothesis)

Evidence for the current wave is from the sources and caveats in `SPEC.md`, many of which are vendor, trade-blog or company self-reports. Read the following as hypotheses:
- Adoption is high and measured delivery gains are modest in several reports.
- The constraint appears to be moving toward review, verification and platform capacity.
- Governance and measurement practices are still forming.

## Side by side

| | Electricity | Dotcom | AI |
| --- | --- | --- | --- |
| Old part replaced | Steam engine | Storefront and paper channel | Human coding |
| Old design kept at first | Central shafts and belts | Existing business model | Existing review, release and approval flow |
| Where friction appeared | Factory layout, training | Fulfillment, fraud, business model | Verification, review capacity, release |
| Governance arrived | Insurers and codes, after fires | Standards and audit rules, after losses | In progress |
| Time to broad payoff | About four decades (David) | Survivors emerged within years of the 2000–2002 fall | Unknown |

## Where the analogies break

- **Speed of change.** Rebuilding factories was physical and slow. Reorganizing software delivery is faster, so the lag may be shorter, though approvals and habits still move at human pace.
- **Determinism.** Electricity behaved the same each time. AI output varies, so verification matters more than it did for power.
- **Market structure.** Electric power became a regulated utility. It is unclear whether AI capability follows that path.
- **No bust is implied.** Whether current valuations correct is outside this note.

## What it suggests, with caution

Across both waves the durable position went to people who understood one concrete constraint deeply, not to those with the technology alone. For ABSORB, that points to D1, D2 and D6 as the dimensions where process and judgment knowledge matters most. This is a reading of two cases, not a test. `VALIDATION.md` is where claims about ABSORB get tested.

## What was not verified

- Henry Ford's moving assembly line (1913) was not checked, so it is left out.
- Amazon Web Services launch dates in 2006 were not checked, so they are left out.
- eBay's feedback system and Pets.com's shipping costs were not checked, so they are left out.
- The "business model," "platform," "ownership," "measurement" and "roles" rows for the dotcom era are interpretation.
- David's paper was read through a web copy and two summaries. Check the original before quoting.

## Sources

Opened on 2026-10-30:

- Paul A. David, "The Dynamo and the Computer: An Historical Perspective on the Modern Productivity Paradox," *AEA Papers and Proceedings*, vol. 80, no. 2, May 1990, pp. 355–361. [Copy via gwern.net](https://gwern.net/doc/economics/automation/1990-david.pdf); [AcaWiki summary](https://acawiki.org/The_dynamo_and_the_computer:_an_historical_perspective_on_the_modern_productivity_paradox)
- [Paul David interview, History News Network](https://www.historynewsnetwork.org/article/paul-david-it-took-decades-for-the-economic-impact)
- [UL (safety organization), Wikipedia](https://en.wikipedia.org/wiki/UL_(safety_organization))
- [125 and counting: the history behind the establishment of the NEC, EC&M](https://www.ecmag.com/section/codes-standards/125-and-counting-important-history-behind-establishment-nec)
- [The dotcom bubble burst, International Banker](https://internationalbanker.com/history-of-financial-crises/the-dotcom-bubble-burst-2000/)
- [Webvan, Wikipedia](https://en.wikipedia.org/wiki/Webvan)
- [PayPal's history of fighting fraud, Plaid](https://fin.plaid.com/paypals-history-of-fighting-fraud)
- [Sarbanes-Oxley Act, Wikipedia](https://en.wikipedia.org/wiki/Sarbanes%E2%80%93Oxley_Act)
- [PCI DSS history, Secureframe](https://secureframe.com/blog/pci-history.md)

Several of these are encyclopedia entries, trade-press articles and vendor blogs, not primary sources. Replace them with primary sources before relying on them in anything formal.
