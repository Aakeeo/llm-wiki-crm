# Meeting Notes — April 7, 2026

**Meeting:** Demo call with RouteAI (intro from Tom Nakamura)
**Attendees:** Mike Torres (VP Product, RouteAI), Our Team
**Duration:** 40 minutes

## Notes

Mike Torres is VP Product at RouteAI, a logistics startup building route optimization software for last-mile delivery companies. They're a Coastal Ventures portfolio company — Tom Nakamura made the introduction during our March check-in.

RouteAI has a solid route optimization engine but their customers keep asking for delivery performance analytics — on-time rates, driver efficiency, cost-per-delivery trends. They've been manually pulling reports from their database and want to embed a self-serve analytics dashboard into their platform.

Key requirements discussed:
- Embeddable analytics dashboard (white-labeled, iframed into their app)
- Real-time data: delivery status, driver location, ETA accuracy
- Historical trend analysis: on-time %, cost per delivery, volume by region
- Multi-tenant: each of their customers (delivery companies) sees only their own data
- API access for customers who want to pull data into their own BI tools

Company details:
- Series A ($8M raised), 25 employees, based in Chicago
- ~200 delivery company customers, processing 500K deliveries/day
- Current analytics: manual SQL queries by their data team, no customer-facing reporting

Mike was impressed with our demo — especially the real-time streaming dashboard and the white-label customization options. He said it's "exactly what our customers have been asking for."

Pricing discussion:
- They want usage-based pricing tied to number of deliveries tracked
- Estimated volume: 500K events/day = ~15M/month
- Ballpark estimate: $70-90K ARR based on our standard tiers

Timeline:
- Mike wants to run a pilot with 3 of their largest customers in May
- Full rollout by Q3 if pilot goes well
- Needs to get buy-in from their CTO (Raj Mehta) — scheduling a technical review next week

## Action Items
- Schedule technical review with Raj Mehta (RouteAI CTO) for next week
- Send multi-tenant architecture documentation
- Prepare pilot proposal for 3 customer accounts
- Send pricing proposal with usage-based tiers
- Update Tom Nakamura on the call
