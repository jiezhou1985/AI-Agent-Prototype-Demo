# Conversation Flow Architecture

Sage uses a **hub-and-spoke** model. Every conversation passes through a central Hub that understands context and routes to the appropriate skill or open conversation. The Hub is always the home base -- conversations leave it, do useful work, and return.

## Architecture Diagram

```
                        +-----------------+
                        |   First Visit?  |
                        +--------+--------+
                                 |
                    yes /        | no
                       /         |
          +-----------+    +-----+------+
          | Onboarding|    |  Check-in  |
          | Flow      |    |  (Recall + |
          | (one-time)|    |  Mood +    |
          +-----+-----+   |  Intent)   |
                |          +-----+------+
                |                |
                +-------+--------+
                        |
                        v
              +-------------------+
              |                   |
              |    HUB            |
              |    (Core Check-in)|
              |                   |
              |  - Mood detection |
              |  - Intent classify|
              |  - Context recall |
              |  - Skill routing  |
              |  - Open chat      |
              |                   |
              +---+----+----+----++
                 /     |    |     \
                /      |    |      \
               v       v    v       v
     +---------+  +----+-+ ++---------+ +----------+
     |purchase- | |grati-| |ad-       | |  ...     |
     |reframe   | |tude  | |literacy  | | (6 more) |
     +---------++ +--+---+ ++---------+ +----+-----+
               |     |      |                |
               |     +--<-->-+  (skills can  |
               |     | transition to each    |
               |     | other mid-convo)      |
               +-----+------+---------------+
                        |
                        v
              +-------------------+
              |    HUB            |
              |    (Wrap-up)      |
              |                   |
              |  - Summarize      |
              |  - Commitment     |
              |  - Follow-up      |
              |  - Profile update |
              +-------------------+
```

## How It Works

### 1. Entry Point

Every conversation begins with one of two entry points:

- **Onboarding** (first visit only): A guided welcome that establishes values, goals, and communication norms. See [onboarding.md](onboarding.md).
- **Check-in** (returning users): Context recall, mood gauge, and intent detection. See [check-in.md](check-in.md).

Both entry points feed into the Hub.

### 2. The Hub (Core Check-in)

The Hub is the brain of every conversation. It is not a visible "screen" to the user -- it is the reasoning layer that runs beneath Sage's responses. The Hub is responsible for:

| Responsibility | What It Does |
|----------------|-------------|
| **Mood detection** | Reads emotional signals from the user's language, energy level, and word choice. Adjusts tone accordingly. |
| **Intent classification** | Determines what the user is here for: a specific impulse, a general check-in, a skill exercise, emotional support, or just chatting. |
| **Context recall** | Pulls in relevant information from past sessions: stated values, goals, pending reflections, previous commitments, patterns over time. |
| **Skill routing** | Selects the most relevant skill to offer based on weighted signals. See [skill-selection.md](skill-selection.md). |
| **Open conversation** | Recognizes when the user just wants to talk, think aloud, or explore a topic without being routed anywhere. |

The Hub never announces itself. The user experiences a natural, flowing conversation. The Hub is the invisible conductor.

### 3. Skill Spokes

Sage has 9 skills, each a self-contained conversational module:

| Skill | Purpose |
|-------|---------|
| `purchase-reframe` | Pause and explore an impulse to buy something |
| `gratitude-practice` | Notice and appreciate what is already present |
| `community-sharing` | Find ways to borrow, share, or connect with others |
| `ad-literacy` | Recognize and deconstruct advertising tactics |
| `self-care-alternatives` | Replace retail therapy with genuine self-care |
| `empathy-connection` | Deepen relationships as a source of fulfillment |
| `goal-alignment` | Check whether a desire aligns with stated values and goals |
| `impact-reflection` | Consider the broader impact of consumption choices |
| `enough-inventory` | Take stock of what you already have and what "enough" means |

#### Skill transitions

Skills are not rigid silos. Mid-conversation, Sage can transition between skills when the conversation naturally calls for it. For example:

- A `purchase-reframe` conversation might reveal that the impulse is driven by loneliness, leading to `empathy-connection`.
- A `gratitude-practice` session might surface awareness that the user already has more than enough, flowing into `enough-inventory`.
- An `ad-literacy` discussion about a specific ad might lead to `goal-alignment` to check whether the advertised product serves the user's values.

Transitions are always gentle and conversational -- never abrupt. Sage might say something like: *"It sounds like this is less about the thing and more about how you're feeling. Want to explore that a bit?"*

### 4. Open Chat

Not everything needs to be routed to a skill. The Hub recognizes when the user:

- Wants to think out loud without structure
- Is sharing something personal that does not map to a skill
- Is asking a factual question
- Just wants company

In these cases, Sage engages as a warm conversational partner without activating any skill. Open chat is always available, and the user can request it explicitly at any time ("I just want to talk" or "no exercises today").

### 5. Wrap-Up

Every conversation returns to the Hub for wrap-up. This phase handles:

- Brief summary of key insights from the session
- Optional commitment check (never pressured)
- Follow-up scheduling if desired
- Profile updates based on new information

See [follow-up.md](follow-up.md) for the full wrap-up flow.

## Design Principles

1. **The user is always in control.** Sage suggests; the user decides. Any skill can be declined. Open chat is always an option.
2. **Conversations should feel natural.** The architecture is invisible to the user. No menus, no "select a skill," no robotic transitions.
3. **Context compounds over time.** Each session builds on the last. Sage remembers values, goals, patterns, and preferences.
4. **Skills are tools, not tracks.** They can be entered, exited, combined, or skipped entirely. The conversation serves the person, not the framework.
5. **Warmth is structural, not decorative.** The architecture itself is designed to be respectful: never forcing, always offering, remembering what matters.
