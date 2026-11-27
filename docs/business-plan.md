# GTA 6 Analysis Channel: Business Plan (working draft)

Status: draft. Revenue figures are third-party estimates and conflict between sources. Replace them with your own numbers after the first 90 days.

## 1. What the business is

A faceless YouTube channel that publishes original analysis and commentary about GTA 6: costs, mechanics, release questions, and comparisons. Every video uses the creator's own script, narration and graphics. Shorts are cut from the long-form video and link back to it.

## 2. Who it serves

- People who bought GTA 6 and want what to do, how systems work, and where to go next
- People waiting on PC or other platforms who want a clear, dated answer
- People interested in the business: costs, markets, release economics
- Veterans comparing GTA 5 and GTA 6

## 3. Why it can work

- Search and trend data show steady demand for GTA 6 questions (vidIQ snapshot, 26 Nov 2026)
- Short hooks are getting high early views on small channels
- Original analysis is the one lane that platforms explicitly allow to earn money from this subject

## 4. Why it can fail

- Platforms reject reused content, so growth must come from original work
- Monetization thresholds are rising in 2027 (YouTube's announced terms)
- Long-form ad income per view is low (third-party RPM about $1.20 to $4.50 per 1,000 views for gaming)
- Interest in launch-week topics fades; the channel has to outlast the news cycle
- Automated claims can hit legitimate GTA content

## 5. Revenue model

Three sources, in order of when they start:

1. **Ad revenue** from long-form, once YouTube Partner Program eligibility is met
2. **Sponsorships and affiliates**, once there's an audience and a track record
3. **Written licences** for specific footage, only if Take-Two or Rockstar grants one (not assumed)

## 6. Illustrative math (replace with real numbers)

Formula: monthly ad revenue = (monthly long-form views ÷ 1,000) × RPM

| Scenario | Monthly long-form views | Assumed RPM | Monthly ad revenue |
|---|---|---|---|
| Low | 20,000 | $1.20 | $24 |
| Mid | 100,000 | $2.50 | $250 |
| High | 500,000 | $4.50 | $2,250 |

Read this as: ad income alone is small until views are high. Sponsorship and affiliate income usually matters first. Treat all three rows as hypotheses to test.

## 7. Costs

| Item | Cost | Notes |
|---|---|---|
| YouTube, Remotion, Google Sheets | Free | Check Remotion's licence terms before commercial use |
| vidIQ, Higgsfield, ElevenLabs | Paid, credit-based | Add only after a free option is shown to be the bottleneck |
| Your time | About 4–5 hours per video once templates exist | The main cost |

Target: no new paid tool until the first five videos are published.

## 8. Production system

- **Engine:** the `gta6-analysis-engine` skill produces a script, scene file, metadata and risk report for each video
- **Tracker:** one row per video, five columns: topic, format, date, average view duration, change made
- **Review:** you read every script and approve before publishing
- **Publish:** YouTube Studio, one video at a time

## 9. Milestones

| Period | Goal | Pass condition |
|---|---|---|
| Days 1–14 | Five Receipts-format videos, all passing the risk check | All five published; tracker complete |
| Days 15–30 | Compare the five on retention; change one variable per video | Clear view on whether the format holds attention |
| Days 31–90 | Pick one or two formats; start the chapter-spine link to long-form | Shorts send viewers to long-form |
| Day 90 | Replace the illustrative math with real numbers | Decision: continue, change format, or stop |

## 10. Risks and controls

| Risk | Control |
|---|---|
| Reused-content demonetization | Original-work rule in the engine; risk check before every publish |
| Copyright claim from a publisher or automated system | No third-party material; keep a log of claims received |
| Rising thresholds | Plan for ad income to start late; sponsorships earlier |
| Topic fades after launch | Mix evergreen questions with news; check trend data weekly |
| Wrong facts | Every claim has a source; corrections go in the description |
| Cost creep | Free tools first; one new paid tool at a time, with a stated reason |

## 11. What's still open

- The first verified number for the Receipts test. This must be checked by you.
- Whether Rockstar or Take-Two will license any footage. Not assumed.
- Real RPM and sponsorship rates for this niche, once there's data.
- Whether to build the MCP wrapper, after the first five videos are done by hand.
