# Viral vs Legacy Music Analysis

This repository contains two complementary analyses that examine music popularity from different perspectives in order to distinguish viral events, breakout artists, and legacy behavior using Spotify data. While both analyses rely on the same residual-based framework, they operate at different levels of granularity and answer different questions.

## 1. Artist-Level Popularity Analysis (ViralArtisAnalysis)
This analysis focuses on identifying **viral breakout artists** and **legacy artists** by examining artist popularity relative to follower count. The goal is to separate short-term momentum from long-term audience size and determine whether an artist is outperforming or underperforming expectations given their scale.

### Methodology

- Artist popularity is modeled as a function of artist follower count using a robust regression.
- An expected popularity baseline is learned for artists of similar follower sizes.
- Residuals are computed as the difference between actual and expected popularity.
- Residuals are standardised into z-scores to identify statistically rare deviations.
- Artists are classified into categories such as:
  - Viral breakout candidates
  - Rising artists
  - Stable or normal artists
  - Legacy artists
  - Declining legacy artists

### What This Analysis Reveals

- Viral artist-level momentum is rare and appears as extreme positive residuals.
- Large follower bases alone do not guarantee high popularity.
- Legacy artists tend to cluster around expected popularity levels, indicating stability rather than growth.

This notebook answers the question:  
**“Which artists are breaking out beyond what their existing audience size would predict?”**

## 2. Track-Level Popularity Analysis(ViralTrackAnalysis)
This analysis shifts the focus from artists to individual tracks in order to identify **viral hit events** and **one-hit wonder candidates**. Track-level popularity captures short-term, event-driven attention that may not translate into sustained artist growth.

### Methodology

- Track popularity is modeled as a function of the artist’s follower count.
- An expected track popularity baseline is estimated for artists of similar size.
- Track-level residuals are computed to measure overperformance or underperformance.
- Residuals are standardised to identify rare viral track events.
- Tracks are classified into categories such as:
  - Viral tracks
  - Emerging viral candidates
  - Normal tracks
  - Underperforming tracks

### What This Analysis Reveals

- Most tracks perform in line with expectations for the artist releasing them.
- True viral tracks appear as rare, extreme positive residuals.
- Viral track success does not always translate into artist-level breakout momentum.

This notebook answers the question:  
**“Which individual tracks go viral relative to the artist’s existing audience?”**
