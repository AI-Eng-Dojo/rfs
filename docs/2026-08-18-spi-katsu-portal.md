---
idea: true
title: "Spi-Katsu Portal"
summary: "A portal for discovering and planning spiritual activities such as wish-making before fan events, combining verified place information with relevant Instagram Reels."
date: 2026-08-18
tags: [consumer, discovery, events, social-media, trust-safety]
lang: en
translation_key: 2026-08-18-spi-katsu-portal
alternate_url: /2026-08-18-spi-katsu-portal-ja.html
credit_name: "Shingo YOSHIDA 吉田真吾"
credit_url: "https://github.com/yoshidashingo"
source_pr: pending
votes: 0
---

# Spi-Katsu Portal

## Summary

"Spi-katsu," short for spiritual activities, includes visiting shrines, temples, or power spots, carrying charms, enjoying fortune-telling, and making wishes. The term is also used for activities connected to Japanese fan culture, such as praying to win a concert ticket, get a good seat, or support an idol's health and success.

Spi-Katsu Portal is a discovery and planning service that turns social-media inspiration into a visit someone can actually make. Users search by purpose, place, date, and time available, then see verified access, hours, costs, cautions, and official sources alongside related Instagram Reels.

For Instagram, the service periodically checks public posts that the official API can retrieve for selected hashtags. Candidates that appear to use a Reel permalink are moderated before publication. The product does not promise immediate updates or complete coverage, and some posts or authors cannot be resolved. Internal controls include account allow/deny lists where the account can be identified, post-level removal, a review queue, and reporting and correction flows.

## Problem

People who want to make a wish before a fan event or casually try a spiritual activity jump between Instagram hashtags, Google Maps, official shrine or temple sites, and event platforms. Short videos are useful for understanding the atmosphere, but they rarely provide structured hours, dates, locations, prices, travel time, or rules. Old posts can lead to incorrect plans.

Hashtag results also mix relevant experiences with unrelated posts, aggressive promotion, expensive sales funnels, and claims that present health or luck outcomes as certain. Conversely, conventional place lists and event sites often lack the first-person context that helps newcomers feel comfortable choosing a destination.

The initial problem is not collecting every piece of spiritual content. It is helping someone quickly choose a safe activity they can do today or this weekend before a concert application, result announcement, or trip.

## Why Now

"Spi-katsu" ranked third in the words category of the 2025 JC-JK Buzzword Awards, making lightweight wish-making behavior among younger people more visible. In January 2026, fan-culture publisher Oshicoco surveyed 503 followers of its Instagram account, and 44.0% said they had done a spiritual activity connected to fandom. The sample is biased toward Oshicoco's followers and cannot be generalized to the population, but it supports testing a purpose-specific discovery experience around fan events.

Instagram's official API offers hashtagged-media discovery for qualifying Professional-account integrations. Production use, however, involves authentication, permissions, and App Review, and the API has limits around recency, ordering, Reel identification, and author information. This creates an opportunity for a product that treats official place information as the source of truth and uses moderated social posts as a discovery layer, instead of scraping and republishing a comprehensive feed.

## First Product

The MVP is a web portal for people aged 18 and over in Tokyo and Kanagawa who have an upcoming concert, stage show, or fan event.

- Search by purpose, such as ticket luck, good seats, an artist's well-being and success, or a pre-trip visit
- Manually register roughly 30 shrines, temples, power spots, and limited-time events
- Show location, opening or event hours, cost, expected visit duration, access, official URL, and the date the information was checked
- Periodically refresh public posts that the official API can retrieve for a small fixed set of hashtags, polling at least daily in the initial operation
- Identify candidate Reel permalinks, then publish them only after moderation, using an official embed or link back to Instagram
- Maintain account allow/deny lists when an author can be resolved, post-level removal in all cases, and a review queue for unresolved posts
- Let users report outdated events, misinformation, fear-based selling, and definitive health or medical claims
- Let users save a place, open maps and directions, and share a plan with a friend
- Clearly label paid placement, referral revenue, or sponsorship separately from ordinary recommendations

The first release excludes a marketplace for readings or consultations, health advice, guarantees about luck or ticket outcomes, and unmoderated automatic publication. Before Meta App Review, the team can validate demand with an allowlist model in which approved or manually selected Reel URLs are registered and displayed.

## Potential Users

The first interview group is fans aged 18 to 29 who live in Tokyo or Kanagawa, or travel there for events. The most relevant participants have previously searched social media for shrines, temples, or activities related to ticket luck, good seats, or an artist's well-being before a concert or stage event.

On the supply side, the team should interview shrines, temples, event organizers, and Creator or Business accounts that want accurate information attached to their content. A venue or religious organization's request not to be listed or not to be described in a certain way takes priority.

## Validation

The first test is a manually operated web experience with around 30 verified places and approved or hand-selected Reels, not a full application.

- Interview at least 15 target users about how they searched before a recent fan event
- Measure the percentage of visitors who save a place or open its map or official site
- Measure whether users return before a concert application, result announcement, or trip
- Follow up to learn whether a viewed place became an actual visit or plan
- Compare time-to-decision and confidence against using Instagram alone
- Track how many candidate posts are held or removed as irrelevant, promotional, dangerous, or author-unresolved
- Before Meta App Review, run a technical spike on API coverage, update latency, Reel detection, and author-resolution rate
- Test whether venues and organizers can easily request a correction or removal

Views of Reels alone do not validate the product if saving, route opening, return visits, and real-world planning do not occur.

## Open Questions

- Should the first scope remain "fandom plus shrine visits," or expand to fortune-telling, meditation, and healing events?
- How can a sustainable business be built if use is infrequent and user spending is low?
- Will a general-purpose portal qualify for Instagram Public Content Access in Meta App Review?
- Can the product identify Reels reliably from Hashtag Search results, and how dependable is permalink-pattern detection?
- When a hashtag result does not expose its author, how much of the requested account-level filtering can be implemented?
- Should approved-account allowlisting be the default instead of denylisting?
- Who rechecks official place and event information, and how often?
- How should the product respect each shrine's or temple's history, policies, and worship practices instead of reducing every place to a source of luck?
- How will moderation detect fear-based selling, expensive funnels, undisclosed promotion, and health or medical misinformation?
- Can account exclusions be based on observable behavior such as spam, false health claims, coercive selling, and repeated violations rather than religion or belief?
- How quickly can the service respond when a post is deleted, made private, or challenged by a rights holder?

## Tags

consumer, discovery, events, social-media, trust-safety

## Sources

- [JC-JK Buzzword Awards](https://jcjkaward.com/) — the placement of "spi-katsu" in the 2025 words category.
- [Oshicoco survey on fandom and spiritual activities](https://corp.oshicoco.co.jp/news/detail/dmfZ1qLP) — a January 2026 survey of 503 followers of the company's Instagram account; it is not representative of the general population.
- [Hands Shibuya renewal news release](https://info.hands.net/news/20260121_seikatsuhenshuzukan.pdf) — an example of merchandising around fandom and spiritual activities.
- [Meta Instagram API: Hashtag Search](https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-facebook-login/hashtag-search) — requirements and limitations for discovering hashtagged public media.
- [Meta Instagram API: Recent Media](https://developers.facebook.com/documentation/instagram-platform/instagram-graph-api/reference/ig-hashtag/recent-media) — fields and constraints for recent-media retrieval.
- [Meta Instagram oEmbed](https://developers.facebook.com/documentation/instagram-platform/oembed) — requirements for official Instagram embeds.
- [Meta Automated Data Collection Terms](https://www.facebook.com/legal/automated_data_collection_terms) — Meta's terms for automated collection.
- [Consumer Affairs Agency: Consumer Contract Act](https://www.caa.go.jp/policies/policy/consumer_system/consumer_contract_act/) — an overview of protections including cancellation of contracts caused by improper solicitation.
- [Consumer Affairs Agency guidance on stealth marketing](https://www.caa.go.jp/policies/policy/representation/fair_labeling/stealth_marketing/) — transparency requirements relevant to paid placement.
- [National Consumer Affairs Center warning about fortune-telling sites](https://www.kokusen.go.jp/news/data/n-20201126_1.html) — examples of high charges and prolonged solicitation.
