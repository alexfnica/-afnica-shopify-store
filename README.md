# AFNICA Fishroom — Shopify E-Commerce Build

A Shopify storefront for a boutique aquarium fish and shrimp breeding business, built from the ground up: store structure, product catalog, community-driven membership perks, and conversion-focused homepage design.

**Live store:** [add your store URL here]
**Role:** Sole builder — store architecture, merchandising, content strategy, and growth features

---

## Overview

AFNICA Fishroom sells rare and selectively-bred aquarium fish, shrimp, and invertebrates (Hypancistrus and Panaqolus plecos, Guppies, Cherry Shrimp) directly from an in-house fishroom. The goal was to turn a hobby breeding operation into a real e-commerce brand — with a store structure that supports both sales and a YouTube-based community.

## What I Built

### Store Architecture & Catalog
- Structured the Shop navigation and created a dedicated **Livestock collection** to properly showcase fish and invertebrates as their own category, separate from plants and dry goods.
- Organized products (existing SKUs) into that collection and audited stock/descriptions for consistency.

### Homepage Redesign
- Benchmarked the homepage structure against an established competitor (Aquarium Co-Op) to identify what to keep, cut, or improve.
- Replaced a low-value "Aquarium Fish Bred By Us" section with a **"Grow Your Fishkeeping Knowledge"** module — a premium, card-based layout linking to the Species Guide and the brand's YouTube channel, positioning the store as an educational resource rather than just a shop.
- Iterated on the design directly with the merchant, moving from plain stacked text to a card-based layout with eyebrow labels, icons, and accent styling for a more premium feel.
- Added a subtle entrance animation to the hero section (fade/slide-in on load) to make the homepage feel more polished on first impression.

### Community & Membership Growth Loop
- Designed a **"Join Club-Membership"** landing page that translates a YouTube channel membership (exclusive videos, livestreams, community chat, discounted merch) into an on-site value proposition, driving signups from store visitors.
- Structured the perks as a scannable 2-column grid rather than a plain list, deliberately omitting price (since membership pricing is managed on YouTube and can change independently of the store).
- Connected the loop end-to-end: **on-site membership page → YouTube membership signup → exclusive 5% store discount code**, issued only to members to keep the perk exclusive rather than publicly visible on the site.
- Created and activated the discount code (`CLUBMEMBER5`, all customers, no expiry set initially) via the Shopify Admin API.

### In Progress
- A **Gift Cards** feature (fixed denominations: 50 / 100 / 150 / 200 lei) — currently blocked on enabling Shopify's native Gift Cards setting, which requires manual activation in the merchant's admin before gift card products can be created via API.

### Data Cleanup & Bug Investigation
- Diagnosed a recurring bug where several product cards in the Livestock collection linked to non-existent `/pages/...` URLs instead of their real `/products/...` pages — traced it back to a batch of orphaned, duplicate Shopify Pages (one per fish species) left over from an earlier, incomplete setup process, sharing the same handle as the real products.
- Deleted 6 orphaned duplicate Pages and 5 stale/incomplete duplicate products (some archived, some draft, some with placeholder pricing) that were cluttering the catalog and, in two cases, forcing the real product onto an ugly auto-suffixed URL (e.g. `-1`).
- Cleaned up the affected product handles so every Livestock product now has a clean, predictable URL matching its title.
- Traced the remaining broken card links to manually-set link overrides at the theme block level (not visible from the collection's default template) and corrected them directly in the theme's source code.
- Along the way, verified and fixed smaller data issues: reactivated two archived products that had stock but weren't visible to customers, restocked a plant variant, split a mispriced product into two properly-priced size variants, and removed an unused empty collection.
- Used a mix of the Shopify Admin GraphQL API (for diagnosis, bulk deletion, and handle fixes) and direct theme code edits (for the final link corrections) — a reminder that AI page builders can leave behind inconsistent state that needs a systematic audit, not just point fixes.

## Tech & Tools

- **Platform:** Shopify (Online Store 2.0)
- **Store editing:** Shopify Sidekick (AI-assisted section/page building inside the theme editor)
- **Backend operations:** Shopify Admin GraphQL API — used to create collections, configure discount codes, and (in progress) gift card products programmatically rather than through manual admin clicks
- **Content:** YouTube (@afnica) as a companion channel for community and behind-the-scenes content, integrated into the store's growth loop

## Key Decisions & Trade-offs

- **Chose a card-based UI over plain text** for both the homepage education section and the membership page — more premium-feeling and more scannable, at the cost of slightly more setup effort in the theme editor.
- **Kept membership pricing off the website** since it lives on YouTube and can change; the store only sells the *outcome* (the discount + perks), not a price that could go stale.
- **Kept the discount code off the site entirely**, distributing it only through YouTube, to preserve it as a genuine member-only perk rather than a public code anyone could grab.
- **Used the Admin API instead of manual admin work** for repeatable, structured tasks (collections, discounts) to keep the process fast and auditable.
- **Verified fixes against the live storefront, not just the admin**, after finding that server-rendered HTML and the JavaScript-corrected version customers actually see can disagree — a reminder to test end-to-end rather than trusting a single layer of the stack.

## What I'd Do Next

- Finish the Gift Cards feature once the native setting is enabled.
- Add customer reviews/social proof to the homepage (inspired by competitor benchmarking).
- Set up basic SEO metadata across product and collection pages.
- Add a video-background or "bubble" animation to the hero for a more distinctive aquarium feel.
- Do a full audit of the remaining catalog for similar leftover duplicate/orphaned content, now that the pattern is known.

---

*Screenshots: [add homepage, membership page, and Livestock collection screenshots here before publishing]*
