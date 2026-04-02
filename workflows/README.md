# Sage Workflow Documentation

This directory contains the conversation workflow specifications for Sage, a mindful consumption AI agent. These documents describe how Sage's conversations flow, how skills are selected, and how continuity is maintained across sessions.

## Files

| File | Description |
|------|-------------|
| [conversation-flow.md](conversation-flow.md) | Hub-and-spoke conversation architecture -- the master blueprint for how all conversations are structured |
| [onboarding.md](onboarding.md) | First-time user experience: welcome, values discovery, goal setting, norm setting, and quick win |
| [check-in.md](check-in.md) | Returning user flow: context recall, mood gauge, intent detection, and routing |
| [skill-selection.md](skill-selection.md) | How Sage decides which of its 9 skills to activate, including signal weights and decision logic |
| [follow-up.md](follow-up.md) | Session wrap-up, commitment checks, follow-up scheduling, and profile adaptation |

## Sage at a Glance

**Purpose:** Help people reduce manufactured wants, counter advertising and consumerism, and encourage human flourishing.

**Tone:** Warm, curious, non-judgmental -- like a thoughtful friend who asks good questions.

**Skills (9):**

1. **purchase-reframe** -- Pause and explore an impulse to buy
2. **gratitude-practice** -- Notice and appreciate what is already present
3. **community-sharing** -- Find ways to borrow, share, or connect with others
4. **ad-literacy** -- Recognize and deconstruct advertising tactics
5. **self-care-alternatives** -- Replace retail therapy with genuine self-care
6. **empathy-connection** -- Deepen relationships as a source of fulfillment
7. **goal-alignment** -- Check whether a desire aligns with stated values and goals
8. **impact-reflection** -- Consider the broader impact of consumption choices
9. **enough-inventory** -- Take stock of what you already have and what "enough" means

## Reading Order

For a first read-through, the recommended order is:

1. `conversation-flow.md` (understand the overall architecture)
2. `onboarding.md` (the entry point for new users)
3. `check-in.md` (the entry point for returning users)
4. `skill-selection.md` (how routing decisions are made)
5. `follow-up.md` (how sessions close and continuity is maintained)
