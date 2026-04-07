---
entity: interaction
date: 2026-04-07
interaction_type: demo
participants:
  - "[[Mike Torres]]"
company: "[[RouteAI]]"
deal: "[[RouteAI - Logistics Analytics]]"
summary: "Product demo for logistics analytics dashboard — Mike impressed, needs CTO buy-in next"
tags: [demo, logistics, coastal-referral]
created: 2026-04-07
---

# RouteAI Demo Call

## Notes

40-minute demo call with Mike Torres (VP Product, RouteAI). [[Tom Nakamura]] from [[Coastal Ventures]] made the introduction.

RouteAI builds route optimization software for last-mile delivery companies. Series A ($8M raised), 25 employees, Chicago. ~200 customers processing 500K deliveries/day.

Their customers are asking for analytics — on-time rates, driver efficiency, cost-per-delivery trends. Currently handled by manual SQL queries by their data team. They want to embed a self-serve dashboard.

Requirements confirmed:
- Embeddable white-labeled dashboard (iframe)
- Real-time: delivery status, driver location, ETA accuracy
- Historical: on-time %, cost per delivery, volume by region
- Multi-tenant: each delivery company sees only their data
- API access for BI tool integration

Mike was impressed with our demo — especially real-time streaming and white-label customization. Said it's "exactly what our customers have been asking for."

Pricing: usage-based tied to deliveries. 500K/day = ~15M events/month. Ballpark $70-90K ARR.

Next steps: Mike needs CTO [[Raj Mehta]] to approve the technical architecture. Technical review next week. Pilot with 3 customers in May if approved.

## Action Items

- Schedule technical review with [[Raj Mehta]] for next week
- Send multi-tenant architecture documentation
- Prepare pilot proposal for 3 customer accounts
- Send pricing proposal with usage-based tiers
- Update [[Tom Nakamura]] on the call

## Raw Source

> [!note]- Raw Source
> # Meeting Notes — April 7, 2026
>
> **Meeting:** Demo call with RouteAI (intro from Tom Nakamura)
> **Attendees:** Mike Torres (VP Product, RouteAI), Our Team
> **Duration:** 40 minutes
>
> Mike Torres is VP Product at RouteAI, a logistics startup building route optimization software for last-mile delivery companies. They're a Coastal Ventures portfolio company — Tom Nakamura made the introduction during our March check-in.
>
> RouteAI has a solid route optimization engine but their customers keep asking for delivery performance analytics — on-time rates, driver efficiency, cost-per-delivery trends. They've been manually pulling reports from their database and want to embed a self-serve analytics dashboard into their platform.
>
> Key requirements: embeddable dashboard, real-time data, historical trends, multi-tenant, API access. Series A ($8M raised), 25 employees, Chicago. ~200 customers, 500K deliveries/day.
>
> Mike impressed with demo. Needs CTO (Raj Mehta) buy-in. Pilot with 3 customers in May. Estimated $70-90K ARR.
