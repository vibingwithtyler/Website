<span class="ai-badge">Written with AI</span>

# ABS Challenge Explorer: Tracking MLB's New Ball-Strike Challenge System

The 2026 MLB season introduced one of the most significant rule changes in years: the Automated Ball-Strike (ABS) challenge system. Players can now challenge ball and strike calls using an automated system that measures whether any part of the baseball crossed any part of the strike zone. I built an interactive dashboard to track every challenge this season.

## What Is the ABS Challenge System?

Starting in 2026, batters and catchers (on behalf of the pitcher/fielding team) each get one challenge per plate appearance to dispute a called ball or strike. A pitch-tracking system makes the final ruling — if the challenge is successful, the call is overturned and the challenger keeps their challenge. If it fails, they lose it for that at-bat.

The key detail: a pitch is considered "in the zone" if **any part of the baseball** (which has a ~1.45 inch radius) crosses **any part of the strike zone**. This means a pitch whose center is slightly outside the rulebook zone can still be a strike, because the edge of the ball clips the edge of the zone.

## What the Explorer Shows

The [ABS Challenge Explorer](https://tylervibes.com/abs-challenge-explorer/) is a full interactive dashboard built in React, pulling live data from the MLB Stats API. Here's what you can dig into:

### Overview Dashboard
The landing page gives you the big picture — total challenges, overturn rates, and breakdowns by pitch type, inning, and batter vs. fielder. **Every card and chart is clickable.** Click "Batter Success" to filter the pitch log to only successful batter challenges. Click a bar in the Daily Trend chart to see only that day's challenges. Click a pitch type to isolate fastballs or sliders. There's also an **Invert** button that flips the filter — so "Batter Success" becomes "Batter Unsuccessful."

### Strike Zone Visualization
Every challenge is plotted on an interactive strike zone graphic. The zone rectangle accounts for ball radius, matching what ABS actually uses. Click any dot to open a detailed popup showing the exact pitch location, miss distance, and all the play context.

### Pitch Log with Full Filtering
The Pitch Log tab gives you a sortable, filterable table of every challenge. You can filter by date, team, inning, batter, pitcher, challenger type, pitch type, result, umpire, whether the pitch was in the zone, velocity range, and miss distance range. It's built for the kind of person who wants to ask "show me all slider challenges by left-handed batters in the 7th inning or later."

### Additional Tabs
- **Miss Distance** — how far off the zone are pitches that get challenged? What's the overturn rate at different distances?
- **Players** — who's challenging the most, and who's the most successful?
- **Teams** — team-level overturn rates and how they compare to the league average
- **Umpires** — which umpires are getting overturned the most?

## How the Data Pipeline Works

A GitHub Actions workflow runs every hour during game hours (12 PM – 12 AM Pacific, March through October). It hits the MLB Stats API's live feed endpoint for every game, looks for reviews with `reviewType: "MJ"` (the code for ABS pitch challenges), and extracts everything — pitch location, zone boundaries, velocity, the ABS ruling, who challenged, the count, the umpire, and more.

The tricky parts were:
- **Deriving the original call** from who challenged (batters challenge strikes, fielders challenge balls)
- **Accounting for ball radius** in zone calculations
- **Getting the pre-pitch count** (the API reports post-pitch count, so you have to reverse-engineer it)
- **Finding the catcher** from the boxscore roster, not the review data

The JSON is committed to GitHub and the frontend fetches it from the raw GitHub URL, so the site updates automatically without any manual uploads.

## Try It Out

The data updates hourly during game days. The more games played, the more interesting the patterns get.

**[Open ABS Challenge Explorer →](https://tylervibes.com/abs-challenge-explorer/)**
