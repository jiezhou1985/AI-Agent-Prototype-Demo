# Sage: Mindful Consumption AI Agent

An AI agent prototype that helps individuals and communities resist manufactured desire, reconnect with genuine needs, and practice contentment -- as a counter to advertising, wasteful consumerism, and the endless cycle of "more."

Sage encourages human flourishing through self-care, empathy, gratitude, community connection, and mindful decision-making.

## Core Philosophy

- **Warm, not preachy.** Sage is a curious friend, not a lecturer.
- **Never shame.** Every impulse is human and valid. Sage explores, never judges.
- **Respect autonomy.** Sage helps people think clearly, then supports whatever they decide.
- **Culturally aware.** Consumerism looks different across economic and cultural contexts.
- **Know your limits.** Sage refers to professionals for addiction, mental health crises, and financial emergencies.

## Repository Structure

```
sage/
├── DESIGN.md                    # Architecture, philosophy, and tone guide
├── prompts/                     # System prompts and safety rails
│   ├── system-prompt.md         # Core agent identity
│   ├── skill-prompts.yaml       # Machine-readable skill prompts
│   └── guardrails.md            # Safety boundaries and edge cases
├── skills/                      # 9 agent skills
│   ├── README.md                # Skills index and interconnections
│   ├── 01-purchase-reframe.md   # Reframe purchase impulses
│   ├── 02-gratitude-practice.md # Gratitude and contentment exercises
│   ├── 03-community-sharing.md  # Borrowing, sharing, co-owning
│   ├── 04-ad-literacy.md        # Deconstruct advertising tactics
│   ├── 05-self-care-alternatives.md # Alternatives to retail therapy
│   ├── 06-empathy-connection.md # Strengthen social connection
│   ├── 07-goal-alignment.md     # Values and goal alignment check
│   ├── 08-impact-reflection.md  # Environmental and social impact
│   └── 09-enough-inventory.md   # Appreciate what you already have
├── workflows/                   # Conversation architecture
│   ├── README.md                # Workflow overview
│   ├── conversation-flow.md     # Hub-and-spoke model
│   ├── onboarding.md            # First-time user experience
│   ├── check-in.md              # Returning user flow
│   ├── skill-selection.md       # How skills are chosen
│   └── follow-up.md             # Session wrap-up and continuity
├── data/                        # Example user and community data
│   ├── README.md                # Data model explanation
│   ├── user-profiles.yaml       # 8 diverse user profiles
│   ├── consumption-patterns.yaml# Consumption archetypes
│   └── community-profiles.yaml  # Community contexts
└── examples/                    # Interaction examples
    ├── README.md                # Examples index
    ├── dialogues/               # Per-skill example conversations
    ├── positive-sequences/      # Multi-session success stories
    └── antipatterns/            # Failure modes with corrections
```

## Getting Started

1. Start with [DESIGN.md](DESIGN.md) for the agent's philosophy and architecture.
2. Read [prompts/system-prompt.md](prompts/system-prompt.md) for Sage's core identity.
3. Browse [skills/](skills/) to see what the agent can do.
4. Review [workflows/](workflows/) for how conversations flow.
5. Explore [examples/](examples/) for concrete interaction sequences.
6. Check [data/](data/) for the user profiles that ground the examples.

## Design Principles

| Principle | In Practice |
|-----------|------------|
| Ask more than tell | Use questions to guide reflection, not directives |
| Mirror their words | Reflect the user's own language back to them |
| Validate first | Acknowledge the feeling before exploring it |
| Distinguish needs from wants | But never dismiss either |
| Celebrate small wins | Without being performative about it |
| Right-size responsibility | Individual choices matter, but systemic change matters more |
