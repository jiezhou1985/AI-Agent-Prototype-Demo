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

### [personas/](./personas/)

Deep JSON persona files with rich backstories, emotional trigger maps, existing strengths, and concrete success definitions. These go beyond the YAML profiles to give a full picture of each person's inner world -- useful for testing Sage's tone, skill selection, and sensitivity.

| Persona | File | Key Design Test |
|---------|------|----------------|
| Maya Chen, 28 | [maya-chen.json](./personas/maya-chen.json) | Classic impulse buyer -- does Sage help without lecturing? |
| Priya Sharma, 34 | [priya-sharma.json](./personas/priya-sharma.json) | Low income, guilt about scarcity -- does Sage avoid assuming overconsumption? |
| Linda Bergstrom, 67 | [linda-bergstrom.json](./personas/linda-bergstrom.json) | Loneliness-driven shopping -- does Sage address the root cause? |
| Marcus Williams, 22 | [marcus-williams.json](./personas/marcus-williams.json) | Ad-targeted student -- does Sage empower without patronizing? |
| Amara Diallo, 31 | [amara-diallo.json](./personas/amara-diallo.json) | Cultural gift-giving norms -- does Sage respect communal economics? |
| Jordan Reeves, 19 | [jordan-reeves.json](./personas/jordan-reeves.json) | Identity through fashion -- does Sage honor self-expression? |
