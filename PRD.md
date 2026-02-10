# Steel Snob Revival - Product Requirements Document

**Project:** Revive steelsnob.com from near-zero to 10,000 monthly organic visitors
**Timeline:** 90 days (Feb 10 - May 10, 2026)
**Owner:** Dror (Tiger Media)
**Executor:** Jawing (AI co-pilot) + sub-agents
**Repo:** https://github.com/Tigermedia/steelsnob

---

## 1. Executive Summary

Steel Snob is a knife niche site with 178 existing articles covering knife laws (50 states), kitchen knives, steel types, outdoor knives, guides, and combat knives. All content is stale (2021-2022). The site has an aged domain, Amazon affiliate setup, and solid plugin stack (Rank Math PRO, WP Rocket). The strategy is to batch-refresh all existing content for 2026 relevance, write 25 targeted new articles for keyword gaps, and fix site foundation issues (E-E-A-T, homepage, internal linking).

---

## 2. Current State

### 2.1 Content Inventory
| Category | Posts | Date Range | Status |
|----------|-------|-----------|--------|
| Knife Laws | 50 | 2020-2021 | All 50 states covered, laws outdated |
| Guides & How-To | 52 | 2019-2022 | Mixed quality, some thin |
| Kitchen Knives | 36 | 2020-2022 | Old product recommendations |
| Outdoors | 23 | 2020-2022 | Old product recommendations |
| Steel Type | 12 | 2022 | Good base, missing newer steels |
| Combat | 9 | 2020-2022 | Old product recommendations |
| **Total** | **178** | | |

### 2.2 Technical Stack
- **CMS:** WordPress
- **Hosting:** Cloudways
- **CDN/DNS:** Cloudflare
- **SEO:** Rank Math SEO PRO
- **Cache:** WP Rocket + Object Cache Pro
- **Internal Links:** Internal Link Juicer (active)
- **Images:** Instant Images
- **Affiliate:** Amazon Associates (tag: steelsnob06-20)

### 2.3 WordPress API
- **Endpoint:** https://steelsnob.com/wp-json/wp/v2/
- **Auth:** Application password stored at `~/.config/wordpress/steelsnob.json`
- **Capabilities:** Full CRUD on posts, pages, categories, media

---

## 3. Goals & KPIs

### 3.1 Primary Goal
**10,000 organic monthly visitors by May 10, 2026**

### 3.2 KPIs
| Metric | Month 1 | Month 2 | Month 3 |
|--------|---------|---------|---------|
| Organic sessions | 1,000-2,000 | 4,000-6,000 | 8,000-10,000 |
| Articles refreshed | 86 | 178 (all) | 178 + maintenance |
| New articles published | 5 | 15 | 25 |
| Keywords in top 10 | 10+ | 30+ | 50+ |
| Keywords in top 100 | 100+ | 300+ | 500+ |
| Affiliate clicks/month | 50+ | 200+ | 500+ |

---

## 4. Workstreams

### WS1: Site Foundation & E-E-A-T
**Priority:** CRITICAL (do first - affects all other work)
**Effort:** 1 sub-agent, ~2 hours

#### Deliverables:
- [ ] **About page** - "About Steel Snob" with site mission, expertise claims, team info
- [ ] **Review methodology page** - "How We Test & Review Knives"
- [ ] **Affiliate disclosure page** - updated, prominent
- [ ] **Privacy policy** - standard, updated for 2026
- [ ] **Homepage redesign** - currently shows only affiliate disclaimer. Needs:
  - Hero section with site value prop
  - Featured/latest articles grid
  - Category showcase (6 categories with top articles)
  - Email signup CTA
- [ ] **Author bio** - create a reusable author block for all articles
- [ ] **Navigation** - verify menu structure covers all categories logically

#### Technical Specs:
- Create pages via WP REST API (`/wp/v2/pages`)
- Homepage can be set as static page via WP settings
- Author bio: add to each post's content at bottom, or use Rank Math author schema

---

### WS2: Knife Laws Refresh (50 articles)
**Priority:** HIGH (highest combined search volume, most templated)
**Effort:** 2 sub-agents working in parallel (25 each), ~3-4 hours total

#### Per-Article Refresh Checklist:
1. **Verify current laws** - research 2025-2026 legislative changes for each state
2. **Update title** - format: "[State] Knife Laws (2026) - What You Can Legally Carry"
3. **Add structured summary box** at top:
   - Legal knife types (bulleted)
   - Restricted/banned types (bulleted)
   - Concealed carry: Yes/No/Permit
   - Blade length limits
   - Preemption: Yes/No
4. **Update body content** - verify accuracy, expand thin sections
5. **Add FAQ section** (5 questions minimum):
   - "Are switchblades legal in [state]?"
   - "Can I carry a concealed knife in [state]?"
   - "What is the maximum blade length in [state]?"
   - "Are butterfly knives legal in [state]?"
   - "Do I need a permit to carry a knife in [state]?"
6. **Enable Rank Math FAQ schema** on the post
7. **Add internal links:**
   - Link to neighboring states
   - Link to `/us-knife-laws/` (overview)
   - Link to relevant knife type articles (switchblades, butterfly knives, etc.)
8. **Update meta description** via Rank Math
9. **Minimum word count:** 1,500 words
10. **Update modified date**

#### API Update Pattern:
```
PUT /wp/v2/posts/{id}
{
  "title": "Updated title",
  "content": "Updated HTML content",
  "date": "original date",  // preserve original publish date
  "modified": "2026-02-10T..."  // WordPress auto-updates this on save
}
```

#### Batch Split:
- **Batch A (25 states):** AL, AK, AZ, AR, CA, CO, CT, DE, FL, GA, HI, ID, IL, IN, IA, KS, KY, LA, ME, MD, MA, MI, MN, MS, MO
- **Batch B (25 states):** MT, NE, NV, NH, NJ, NM, NY, NC, ND, OH, OK, OR, PA, RI, SC, SD, TN, TX, UT, VT, VA, WA, WV, WI, WY

---

### WS3: Kitchen Knives Refresh (36 articles)
**Priority:** HIGH (best affiliate revenue potential)
**Effort:** 1 sub-agent, ~3-4 hours

#### Per-Article Refresh Checklist:
1. **Update title** with 2026: "Best [X] Knife (2026) - Top Picks Reviewed"
2. **Research current top products** - check Amazon for:
   - Current bestsellers in category
   - Products with 4.5+ stars and 500+ reviews
   - Price range coverage ($, $$, $$$)
3. **Replace outdated product recommendations:**
   - New Amazon affiliate links with tag `steelsnob06-20`
   - Updated pricing
   - Current product images (use Amazon product image URLs)
4. **Add/update comparison table** at top of buyer guides:
   - Product name, price range, key feature, our verdict
5. **Add "What to Look For" buying guide section** if missing
6. **Add FAQ section** (3-5 questions with schema)
7. **Expand thin content** to 2,000+ words for buyer guides
8. **Add internal links** to related kitchen articles and steel type guides
9. **Update meta description**

#### Key Articles (highest priority within kitchen):
1. `best-kitchen-knife-set` - massive keyword
2. `best-japanese-knives` - high buyer intent
3. `best-santoku-knife` - popular search
4. `best-nakiri-knife` - already has good structure
5. `best-steak-knife` - high affiliate potential
6. `best-ceramic-knives` - trending topic
7. `best-cleaver-knife` - good volume
8. `best-fillet-knife` - enthusiast audience
9. `best-boning-knife` - specific buyer intent
10. `best-german-kitchen-knives` - brand-focused

---

### WS4: Steel Type Refresh + New Comparisons (12 existing + 10 new)
**Priority:** HIGH (brand identity, low competition keywords)
**Effort:** 1 sub-agent, ~4-5 hours

#### Existing Steel Articles (refresh):
For each of the 12 "What is X Steel?" articles:
1. **Update with 2026 data** - any new test results, industry developments
2. **Add comparison section** - how this steel compares to 2-3 alternatives
3. **Add "Best knives in X steel" section** with affiliate links
4. **Add steel specs table:**
   - Hardness (HRC)
   - Edge retention (1-10)
   - Toughness (1-10)
   - Corrosion resistance (1-10)
   - Ease of sharpening (1-10)
5. **Add FAQ section with schema**
6. **Interlink all 12 steel articles** to each other
7. **Minimum 2,000 words**

#### New Steel Comparison Articles (write):
| # | Title | Slug |
|---|-------|------|
| 1 | S30V vs S35VN - Complete Steel Comparison | s30v-vs-s35vn |
| 2 | MagnaCut vs M390 - Which Premium Steel Wins? | magnacut-vs-m390 |
| 3 | D2 vs S30V - Detailed Comparison | d2-vs-s30v |
| 4 | 154CM vs S30V - Which Should You Choose? | 154cm-vs-s30v |
| 5 | 440C vs VG-10 - Budget Steel Breakdown | 440c-vs-vg10 |
| 6 | AUS-8 vs 8Cr13MoV - Budget Steel Showdown | aus-8-vs-8cr13mov |
| 7 | CPM 3V vs CPM 4V - Tool Steel Compared | cpm-3v-vs-cpm-4v |
| 8 | MagnaCut Steel - The Complete Guide (2026) | magnacut-steel-guide |
| 9 | S45VN Steel - Everything You Need to Know | s45vn-steel-guide |
| 10 | Best Knife Steel (2026) - Ultimate Guide & Rankings | best-knife-steel-2026 |

#### New Article Template (Steel Comparison):
```
# [Steel A] vs [Steel B] - Complete Comparison (2026)

## Quick Answer (featured snippet bait)
[2-3 sentence summary with clear winner per use case]

## Steel Specifications Comparison Table
| Property | Steel A | Steel B |
|----------|---------|---------|
| Hardness (HRC) | X | Y |
| Edge Retention | X/10 | Y/10 |
| Toughness | X/10 | Y/10 |
| Corrosion Resistance | X/10 | Y/10 |
| Ease of Sharpening | X/10 | Y/10 |
| Price Range | $ | $$ |

## Edge Retention [detailed section]
## Toughness [detailed section]
## Corrosion Resistance [detailed section]
## Ease of Sharpening [detailed section]
## Price & Value [detailed section]
## Best Knives in [Steel A] [3 picks with affiliate links]
## Best Knives in [Steel B] [3 picks with affiliate links]
## Which Steel Should You Choose?
## FAQ (5 questions, schema enabled)
```

**Word count target:** 2,500-3,000 per comparison article

---

### WS5: Guides Refresh (52 articles)
**Priority:** MEDIUM (high volume but diverse topics)
**Effort:** 2 sub-agents (26 each), ~3-4 hours total

#### Per-Article Refresh Checklist:
1. **Update title** for freshness and CTR
2. **Verify factual accuracy** - any outdated claims?
3. **Expand thin sections** - target 1,500w minimum
4. **Add step-by-step structure** for how-to articles (with HowTo schema)
5. **Add FAQ section** (3-5 questions with schema)
6. **Update/add images** with proper alt text
7. **Add internal links** to related articles
8. **Add product recommendations** where relevant (affiliate opportunity)
9. **Update meta description**

#### Sub-categories to handle:
- **Sharpening guides** (5 articles) - highest volume
- **Knife care/maintenance** (8 articles) - evergreen
- **Knife identification/value** (3 articles) - collector audience
- **Hunting guides** (10 articles) - outdoor enthusiast
- **General knife knowledge** (15 articles) - informational
- **Brand comparisons** (3 articles) - buyer intent
- **Miscellaneous** (8 articles)

---

### WS6: Outdoors + Combat Refresh (32 articles)
**Priority:** MEDIUM
**Effort:** 1 sub-agent, ~2-3 hours

#### Per-Article Refresh:
Same checklist as Kitchen (WS3) for buyer guides.
Same checklist as Guides (WS5) for informational articles.

Focus on:
- Updating "Best X of 2022" titles to 2026
- Replacing dead product links
- Adding FAQ schema
- Cross-linking outdoor articles together

---

### WS7: New Kitchen & EDC Articles (15 articles)
**Priority:** MEDIUM (after refresh waves complete)
**Effort:** 1 sub-agent, ~4-5 hours

Articles listed in PLAN-v2.md sections "Kitchen Gaps" and "EDC & Brands."

#### Template (Buyer Guide):
```
# Best [Product] (2026) - Top [N] Picks Reviewed

## Our Top Picks (comparison table)
## Detailed Reviews
### 1. [Product] - Best Overall
### 2. [Product] - Best Value
### 3. [Product] - Premium Pick
### 4. [Product] - Budget Pick
### 5. [Product] - Also Great
## What to Look For in a [Product]
## FAQ (5 questions, schema)
## Final Verdict
```

**Word count target:** 2,500-3,500 per article

---

## 5. Technical Requirements

### 5.1 WordPress API Usage
All content operations via REST API:
- **Read:** `GET /wp/v2/posts/{id}` with `_fields` for efficiency
- **Update:** `PUT /wp/v2/posts/{id}` with updated `title`, `content`, `excerpt`
- **Create:** `POST /wp/v2/posts` with `status: "draft"` for review, then publish
- **Auth:** Basic auth with application password

### 5.2 Content Standards
- **Minimum word count:** 1,500 (informational), 2,500 (buyer guides)
- **Every article must have:**
  - Table of contents (handled by Rank Math/TOC Plus)
  - FAQ section with Rank Math schema
  - At least 3 internal links to related articles
  - Meta description optimized for CTR
  - Focus keyword set in Rank Math
  - At least 1 image with descriptive alt text
- **Affiliate links:** Amazon tag `steelsnob06-20`, rel="nofollow sponsored"
- **No AI slop:** Content must read naturally, include specific product details/specs, and demonstrate genuine expertise

### 5.3 SEO Requirements
- **Title format:** "[Primary Keyword] - [Benefit/Year]" (under 60 chars)
- **Meta description:** 150-160 chars, includes keyword, compelling CTA
- **URL structure:** Keep existing slugs (don't change URLs!)
- **Schema:** FAQ on all articles, HowTo on tutorial articles, Product on reviews
- **Internal linking:** Every article links to at least 3 related articles

### 5.4 Rank Math Configuration
- Focus keyword set for each article
- SEO score target: 80+
- FAQ blocks use Rank Math FAQ block format for auto-schema

---

## 6. Sub-Agent Deployment Plan

### Phase 1: Foundation + First Waves (NOW)
| Agent | Label | Workstream | Articles | Model |
|-------|-------|-----------|----------|-------|
| 1 | `ss-foundation` | WS1: Site Foundation | Pages | Sonnet |
| 2 | `ss-laws-batch-a` | WS2: Knife Laws A-MO | 25 articles | Sonnet |
| 3 | `ss-laws-batch-b` | WS2: Knife Laws MT-WY | 25 articles | Sonnet |
| 4 | `ss-kitchen` | WS3: Kitchen Refresh | 36 articles | Sonnet |
| 5 | `ss-steel` | WS4: Steel Refresh + New | 22 articles | Sonnet |

### Phase 2: Remaining Refresh (after Phase 1)
| Agent | Label | Workstream | Articles | Model |
|-------|-------|-----------|----------|-------|
| 6 | `ss-guides-a` | WS5: Guides batch 1 | 26 articles | Sonnet |
| 7 | `ss-guides-b` | WS5: Guides batch 2 | 26 articles | Sonnet |
| 8 | `ss-outdoor-combat` | WS6: Outdoors + Combat | 32 articles | Sonnet |

### Phase 3: New Content (after Phase 2)
| Agent | Label | Workstream | Articles | Model |
|-------|-------|-----------|----------|-------|
| 9 | `ss-new-kitchen-edc` | WS7: New articles | 15 articles | Sonnet |

---

## 7. Progress Tracking

### Checkpoint Protocol
Each sub-agent MUST use `task-checkpoint.sh` for progress tracking.

### Progress Updates
- Sub-agents report completion to Discord #jw-25-steelsnob
- Main agent synthesizes progress and updates Dror
- Daily progress logged in `memory/2026-02-XX.md`

### Completion Criteria per Article
An article is "done" when:
- [x] Title updated with year/freshness
- [x] Content refreshed/expanded to minimum word count
- [x] FAQ section added with schema
- [x] Internal links added (3+ minimum)
- [x] Meta description updated
- [x] Product links verified (for buyer guides)
- [x] Published via API

---

## 8. Risk Mitigation

| Risk | Mitigation |
|------|-----------|
| API rate limiting | Space requests 1-2 seconds apart, batch in groups of 10 |
| Content quality | Spot-check 10% of updated articles via browser |
| Broken affiliate links | Verify Amazon URLs return 200 before publishing |
| Google penalizing mass updates | Stagger updates over days, not all at once |
| Sub-agent context overflow | Use checkpoints, split into smaller batches |
| Outdated legal information | Add disclaimer: "This is not legal advice. Laws change. Verify with local authorities." |

---

## 9. Success Criteria

### 90-Day Targets
- [ ] All 178 existing articles refreshed for 2026
- [ ] 25 new articles published
- [ ] All articles have FAQ schema
- [ ] Internal linking network complete
- [ ] About page + methodology page live
- [ ] Homepage redesigned
- [ ] 10,000 monthly organic visitors (or clear upward trajectory)
- [ ] Affiliate revenue generating $100+/month

### Definition of Done (Project)
The project is "done" when all 203 articles (178 refreshed + 25 new) are live, the site foundation is solid, and organic traffic shows consistent week-over-week growth toward the 10K target.
