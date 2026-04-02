# Sage Skills

Nine skills covering the full spectrum of mindful consumption -- from reactive (an impulse arrives) to proactive (building daily practices) to systemic (community and environmental impact).

## Skills Index

| # | Skill | ID | When It Activates |
|---|-------|----|-------------------|
| -- | [Session Start](session-start.md) | `session-start` | Beginning of a new conversation / `/session-start` |
| 01 | [Purchase Reframe](01-purchase-reframe.md) | `purchase-reframe` | User mentions wanting to buy something |
| 02 | [Gratitude Practice](02-gratitude-practice.md) | `gratitude-practice` | Dissatisfaction, envy, or daily practice |
| 03 | [Community Sharing](03-community-sharing.md) | `community-sharing` | Rarely-used items, community interest |
| 04 | [Ad Literacy](04-ad-literacy.md) | `ad-literacy` | User encountered marketing/advertising |
| 05 | [Self-Care Alternatives](05-self-care-alternatives.md) | `self-care-alternatives` | Emotional spending, retail therapy |
| 06 | [Empathy & Connection](06-empathy-connection.md) | `empathy-connection` | Isolation, social comparison |
| 07 | [Goal Alignment](07-goal-alignment.md) | `goal-alignment` | Significant purchases, decision points |
| 08 | [Impact Reflection](08-impact-reflection.md) | `impact-reflection` | Sustainability questions, ethical concerns |
| 09 | [Enough Inventory](09-enough-inventory.md) | `enough-inventory` | Feeling of lack, periodic review |

## How Skills Connect

Skills can transition to other skills mid-conversation. The common pathways:

```
Purchase Reframe ──→ Self-Care Alternatives (if emotional trigger found)
                 ──→ Goal Alignment (if values tension found)
                 ──→ Enough Inventory (if "I don't have enough" feeling)

Ad Literacy ──→ Purchase Reframe (if desire persists after deconstruction)

Self-Care Alternatives ──→ Empathy & Connection (if loneliness is the root)
                       ──→ Gratitude Practice (for grounding)

Empathy & Connection ──→ Community Sharing (for practical connection)

Goal Alignment ──→ Impact Reflection (if environmental values surface)

Enough Inventory ──→ Gratitude Practice (natural extension)
                 ──→ Community Sharing (for items to share)
```

## Skill Schema

Every skill file follows a consistent structure:

```yaml
name: Human-readable skill name
id: kebab-case identifier
trigger_conditions: List of signals that activate this skill
system_prompt: The prompt injected when this skill is active
behavior:
  entry: How the skill begins
  core_loop: The main interaction pattern
  exit: How the skill concludes
  transitions: Which skills it can hand off to
tone_guidance: Specific tone notes for this skill
```
