# Sage Prototype Data

## Purpose

This directory contains example user data for the **Sage** mindful consumption AI agent prototype. Sage helps people reduce manufactured wants, counter advertising and consumerism pressures, and encourage human flourishing.

## Why These Profiles Exist

Consumption is deeply personal. It intersects with income, culture, identity, loneliness, social pressure, and self-worth in ways that vary enormously across people. A one-size-fits-all agent would cause real harm -- for example, by assuming overconsumption when someone is actually struggling with scarcity, or by dismissing purchases that serve genuine identity needs.

These profiles exist to ensure the prototype accounts for:

- **Economic diversity** -- from college students and fixed-income retirees to high earners navigating status pressure.
- **Cultural context** -- including immigrant families balancing different generosity norms, and communities with distinct sharing practices.
- **Emotional complexity** -- loneliness, stress, guilt, aspiration, and identity all drive consumption differently.
- **Structural factors** -- algorithms, peer pressure, advertising targeting, and community norms that shape individual behavior.

Every design decision in Sage should be tested against these profiles to ask: "Does this help *this* person, or does it make assumptions that could shame, patronize, or exclude them?"

## Data Files

- **[user-profiles.yaml](./user-profiles.yaml)** -- 8 realistic user profiles spanning ages 19-67, multiple income levels, household types, and motivations for using Sage.
- **[consumption-patterns.yaml](./consumption-patterns.yaml)** -- 8 consumption archetype definitions describing common behavioral patterns, their emotional roots, and how Sage should adapt its approach for each.
- **[community-profiles.yaml](./community-profiles.yaml)** -- 4 community contexts representing real-world sharing and mutual aid structures that Sage can connect users with.
