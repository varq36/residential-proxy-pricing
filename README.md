# cheapest residential proxies: how to get real residential IPs at a flat $1/GB with no subscription, no expiring traffic, and no bulk commitment

Every "cheapest residential proxies" list starts with a number that looks impossible. A dollar a gigabyte. Forty cents. Thirty-two cents. Then you click through, hit the plan table, and discover you have to buy a terabyte before any of those numbers apply.

That's the actual problem to solve here. Not "which provider is cheapest" — that question has no fixed answer, because the cheapest provider changes with your volume, sometimes by a factor of ten. The useful question is: what will *you* pay, at *your* monthly traffic, once the minimum purchase and the plan granularity are factored in?

For anyone buying under about 50 GB a month, one provider sits at the bottom of that calculation, and it's the one this guide digs into: DataImpulse, at a flat $1/GB for residential traffic with a $5 minimum, pay-as-you-go, and traffic that never expires.

## The advertised floor is almost never the price you can buy

Proxy marketing has a standard move: quote the last rung of the volume ladder. A few examples from the current public pricing pages:

- **IPRoyal** advertises $1.75/GB. A single gigabyte costs $7. The $1.75 rate is available from 10 TB.
- **Webshare** advertises $1.40/GB, which is the 3,000 GB row — about $4,200 a month. At 1 GB you pay $3.50.
- **Decodo** puts $2/GB in its page title and meta description; the entry plan on the same page is $3.75/GB, and $2/GB only appears at the top of the volume ladder.
- **Bright Data** shows $2.50/GB in its navigation. On its own pricing cards the numbers are $4, $4, $3 and $3 per GB against a list price of $8 — and the lower rate is a coupon that runs for three months.
- **SOAX** has no per-GB rate below a $5/GB tier-1 price, and its cheapest paid plan carries a $200 monthly fee.

Bright Data and Oxylabs are the two exceptions worth noting: Oxylabs quotes $6/GB and genuinely sells 5 GB at $6/GB; Bright Data's $8/GB pay-as-you-go is a real price you can check out with. They're also the two most expensive networks in this comparison. That trade — an honest headline versus a cheap one — matters more than it looks, because a proxy budget that's wrong by 4× wrecks the unit economics of a scraping pipeline faster than any other line item.

## What actually sets your invoice: four mechanisms

Strip out the branding and nearly all of the price difference between providers comes down to four things.

**1. The entry minimum.** Below roughly 10 GB a month, the minimum purchase *is* your price, and the per-GB rate is decoration. A provider with a $200 monthly floor costs 40× more than a $5 pay-as-you-go pack when you only need 5 GB.

**2. Plan granularity.** Oxylabs looks cheap at 5 GB ($30) and expensive at 50 GB, because the smallest plan that covers 50 GB is a 125 GB plan — you buy 75 GB you don't need. Evomi's entry plan is 100 GB, so at 5 GB most of that spend is dead weight; at 50 GB it's joint-cheapest. Same vendor, same price list, opposite verdicts.

**3. Targeting multipliers.** Country-level targeting is normally bundled in. City, state, ZIP and ASN targeting often isn't. On DataImpulse's standard residential plan, traffic routed through advanced filters (city, state, ZIP, ASN) is billed at **2× the standard rate** — so a $1/GB plan becomes an effective $2/GB the moment you need city-level precision. That's still cheaper than most providers' base rate, but you should know it before you build the budget.

**4. Billable traffic includes retries and headers.** You're billed for what passes through the proxy, not for the rows you keep. Request headers, POST data, response headers and every failed attempt all count. A scraper with a 40% block rate doesn't pay 40% more — it pays for all the retries plus the overhead on every one of them.

## Where the cheap providers actually land

Rates below are taken from each provider's public pricing pages. Everything in this market moves, so treat this as a starting position rather than a quote.

| Provider | What you pay at ~5 GB | At mid volume | At 1 TB | Traffic expiry |
| --- | --- | --- | --- | --- |
| **DataImpulse** | $1.00/GB — $5 buys 5 GB | $1.00/GB — 50 GB for $50 | $0.80/GB — 1 TB for $800 | Never expires |
| Webshare | $3.50/GB at 1 GB | $2.25/GB — 100 GB for $225 | $1.50/GB at 1,000 GB | Monthly billing |
| Rayobyte | $3.50/GB (1–49 GB band) | $2.00/GB (50–249 GB) | $0.70/GB (1,000–4,999 GB) | Plan-based |
| Decodo | $3.75/GB entry plan | $2.75/GB — 100 GB for $275 | $2/GB top tier | Monthly billing |
| IPRoyal | $7.00/GB at 1 GB | $5.25/GB at 10 GB | $1.75/GB only from 10 TB | Never expires |
| Oxylabs | $6.00/GB — 5 GB for $30 | $4.00/GB — 125 GB for $500 | $2.50/GB — $2,500 | Monthly billing |
| Bright Data | ~$8.00/GB pay-as-you-go | ~$4.00/GB with a three-month coupon | Commitment plans $499–$1,999/month | Unused commitment doesn't roll over |

Read that column by column rather than row by row. At 5 GB, DataImpulse at $1.00/GB is the cheapest buy on the board, and the gap isn't marginal — it's 3.5× to 8×. At 1 TB, the flat-rate vendors lose their edge, because a flat rate by definition gives you no volume discount, and metered ladders start to win. Rayobyte's $0.70/GB at that scale is below DataImpulse's $0.80/GB.

If you're buying at 5 GB or 50 GB, 👉 [👉 check the current DataImpulse residential packs](https://bit.ly/dataimPulse) and compare the effective rate against your own monthly traffic. If you're genuinely pushing a terabyte a month, that's the point where you request custom pricing rather than buying off the shelf — DataImpulse's custom residential tier starts at $4,000 for 5 TB and above.

## What $1/GB buys from DataImpulse

The rate isn't the whole offer, and it's worth knowing what's in the box before deciding it's too good to be true.

- **Pool size and sourcing.** 90M+ residential IPs across 195 countries, drawn from first-party pools rather than resold third-party networks. Every node joins with documented user consent — that's the "ethically sourced" claim, and it has a practical consequence: IPs with less shared abuse history get blocked less often on high-security sites.
- **Targeting.** Country-level targeting is free and set as a URL parameter rather than a dashboard toggle, so you don't need a separate configuration per location. City, state, ZIP and ASN are available on standard residential at the 2× billing multiplier described above.
- **Sessions.** Rotating sessions hand you a fresh IP per request; sticky sessions hold one IP on a dedicated port for 1 to 120 minutes, with a 30-minute default and ports in the 10000–20000 range. Rotating and sticky both work over HTTP(S) and SOCKS5.
- **Billing.** Pay-as-you-go. No subscription, no monthly minimum beyond the $5 top-up, and purchased traffic doesn't expire — you can buy 50 GB in a heavy quarter and still have 12 GB left three months later.
- **Support and track record.** 24/7 human support via chat and email, API access, IP whitelisting, and a dashboard with per-plan usage graphs. The provider publishes a 99.51% success rate and holds a 4.8/5 rating on G2. TechRadar's review of the service reported a consistently high scraping success rate from the residential pool in its own tests, and singled out the non-expiring pay-as-you-go model as the main differentiator against Bright Data, Oxylabs and Decodo.

There's no free trial. Access starts at the $5 minimum, which is the honest version of a trial: 5 GB of real residential traffic. Intro plans bought by card carry a 7-day money-back guarantee, provided less than 80% of the traffic has been consumed. Crypto purchases on Intro plans are non-refundable.

## Every DataImpulse plan on the pricing page

DataImpulse sells four proxy types, each with its own pack sizes. Tier labels differ by product, so the table lists packs by traffic volume, which is what actually hits your invoice.

| Proxy type | Pack | Price | Effective rate | Billing | Get it |
| --- | --- | --- | --- | --- | --- |
| Residential | 5 GB | $5 | $1.00/GB | Pay-as-you-go | [ start with the 5 GB residential pack](https://bit.ly/dataimPulse) |
| Residential | 50 GB | $50 | $1.00/GB | Pay-as-you-go | [ buy 50 GB of residential traffic](https://bit.ly/dataimPulse) |
| Residential | 1 TB | $800 | $0.80/GB (20% volume discount) | Pay-as-you-go | [ take the 1 TB residential rate](https://bit.ly/dataimPulse) |
| Residential | 5 TB+ | From $4,000 | Custom | Custom quote | [ request custom residential pricing](https://bit.ly/dataimPulse) |
| Datacenter | 10 GB | $5 | $0.50/GB | Pay-as-you-go | [ grab the 10 GB datacenter pack](https://bit.ly/dataimPulse) |
| Datacenter | 100 GB | $50 | $0.50/GB | Pay-as-you-go | [ buy 100 GB of datacenter traffic](https://bit.ly/dataimPulse) |
| Datacenter | 1 TB | $450 | $0.45/GB | Pay-as-you-go | [ check the 1 TB datacenter tier](https://bit.ly/dataimPulse) |
| Datacenter | 5 TB+ | From $2,250 | Custom | Custom quote | [ get a datacenter quote](https://bit.ly/dataimPulse) |
| Mobile (5G/4G/3G/LTE) | 2.5 GB | $5 | $2.00/GB | Pay-as-you-go | [ try mobile proxies from $5](https://bit.ly/dataimPulse) |
| Mobile (5G/4G/3G/LTE) | 25 GB | $50 | $2.00/GB | Pay-as-you-go | [ buy 25 GB of mobile traffic](https://bit.ly/dataimPulse) |
| Mobile (5G/4G/3G/LTE) | 1 TB | $1,600 | $1.60/GB (20% volume discount) | Pay-as-you-go | [ see the 1 TB mobile tier](https://bit.ly/dataimPulse) |
| Mobile (5G/4G/3G/LTE) | 5 TB+ | From $8,000 | Custom | Custom quote | [ request custom mobile pricing](https://bit.ly/dataimPulse) |
| Premium residential | 1 GB | $5 | $5.00/GB | Pay-as-you-go | [ test premium residential with 1 GB](https://bit.ly/dataimPulse) |
| Premium residential | 10 GB | $50 | $5.00/GB | Pay-as-you-go | [ buy 10 GB of premium residential](https://bit.ly/dataimPulse) |
| Premium residential | 5 TB+ | From $20,000 | Custom | Custom quote | [ ask about the premium residential tier](https://bit.ly/dataimPulse) |

Two things worth flagging in that table.

First, the volume discount threshold is high. The 20% cut on residential and mobile only kicks in at 1 TB, which means the plans most people buy — 5 GB, 50 GB — carry no discount at all. That's the trade for a flat $1/GB: no discount ladder, but also no commitment.

Second, premium residential is not the cheap option, and it isn't sold as one. At $5/GB it costs five times the standard residential rate, and if your only reason for considering it is city-level targeting, standard residential at the 2× multiplier still comes out cheaper per gigabyte ($2/GB effective). Premium buys the other things: a high-speed pool, sub-50ms response times, all targeting options bundled with no surcharge, and a dedicated account manager. If you're running an ad-verification workflow where a block costs more than the bandwidth, that price difference is easy to justify. If you're running a nightly price scraper, it isn't.

## Setting it up for $5

The barrier to testing this yourself is one top-up. The flow, per the provider's own onboarding:

1. Create an account and open the dashboard.
2. Choose a proxy type — residential, datacenter, mobile or premium residential.
3. Top up the balance. $5 activates 5 GB of residential traffic and there's no subscription attached.

The endpoint format is standard, with targeting and session control passed in the username string:

text
# Rotating: new IP per request
http://USERNAME:PASSWORD@gw.dataimpulse.com:823

# Sticky: same IP for the session
http://USERNAME:PASSWORD_session-abc123@gw.dataimpulse.com:823

# Country targeting
http://USERNAME:PASSWORD_country-us@gw.dataimpulse.com:823

# City targeting (billed at 2× on standard residential)
http://USERNAME:PASSWORD_country-us_city-newyork@gw.dataimpulse.com:823


Selenium, Puppeteer and Scrapy integrations are documented, and most proxy managers and antidetect browsers accept the same format.

Before you scale anything, do one measurement: run a week on pay-as-you-go and log gigabytes per 1,000 successful records, not bytes per payload. That single number tells you whether $1/GB is genuinely cheap for your workload, because a provider at $1/GB with a 60% success rate can cost more per usable record than one at $3/GB that almost never fails.

## Where the cheap option genuinely isn't the right one

Being clear about the limits is more useful than another paragraph about how affordable everything is.

- **You need a free trial with no card.** DataImpulse doesn't offer one. The $5 intro pack is the entry point, with a 7-day card refund if you've used under 80% of the traffic.
- **You need city-level targeting at terabyte scale.** The 2× multiplier turns $1/GB into $2/GB on standard residential, and premium residential at $5/GB with everything bundled is the cleaner answer at very high volume — or a custom quote.
- **You need enterprise procurement.** DataImpulse's largest standard tiers are self-serve up to 1 TB, with custom pricing above 5 TB. Providers like Bright Data run KYC with possible video verification and offer a 7-day trial for registered businesses; if compliance paperwork matters more than the per-GB rate, that's a different purchase.
- **You need an integrated scraper, not bandwidth.** If the proxy should come bundled with the scraper, tools like Apify Proxy at $8/GB are more expensive per gigabyte but remove a second vendor and a second invoice.

For the far more common case — a developer, a small agency or a data team pulling somewhere between 5 GB and 200 GB a month, running bursts rather than a steady stream — the arithmetic is unglamorous and lopsided. Nothing else on the board gets you real residential IPs at $1/GB with a $5 entry, and nothing else lets you stop using it for two months without losing the balance.

If that's your shape, 👉 [👉 open DataImpulse and start with $5 of residential traffic](https://bit.ly/dataimPulse). If you're closer to a terabyte a month, 👉 [👉 look at the full DataImpulse pricing tiers](https://bit.ly/dataimPulse) and ask for a custom quote instead — at that scale, the public per-GB numbers are a starting position, not a price.

## Quick answers

**Is a flat $1/GB suspiciously cheap?** It's below the market's $3–$8/GB residential norm, and the reasons are structural: first-party IP pools instead of resold networks, no subscription billing layer, and thin margins on volume rather than revenue from minimum commitments. The trade-offs — no free trial, a 2× targeting multiplier, volume discounts only from 1 TB — are listed on the pricing page rather than hidden behind a sales call.

**Do I have to commit monthly?** No. There's no subscription and no monthly minimum beyond the $5 top-up. Unused traffic stays in the account.

**What's the smallest real purchase?** $5. That's 5 GB of residential, 10 GB of datacenter, 2.5 GB of mobile, or 1 GB of premium residential.

**Which proxy type should I start with?** Residential, unless your targets don't block datacenter IPs — in which case datacenter at $0.50/GB gets you twice the traffic for the same $5. Mobile is for the cases that specifically need carrier-grade IPs, and it costs twice what residential does.
