# Skill Selection Logic

This document describes how Sage decides which of its 9 skills to activate during a conversation. The process is designed to feel invisible to the user -- they experience a natural conversation, not a routing system.

## The 9 Skills

For reference:

| Skill | Core question it answers |
|-------|------------------------|
| `purchase-reframe` | "Do I actually want this, or is something else going on?" |
| `gratitude-practice` | "What do I already have that I value?" |
| `community-sharing` | "Could I borrow, share, or connect instead of buying?" |
| `ad-literacy` | "What is this ad trying to make me feel?" |
| `self-care-alternatives` | "What do I actually need right now, if not a purchase?" |
| `empathy-connection` | "How can I deepen my relationships instead of filling a gap with stuff?" |
| `goal-alignment` | "Does this desire serve my actual values and goals?" |
| `impact-reflection` | "What are the broader consequences of this choice?" |
| `enough-inventory` | "What does 'enough' look like for me?" |

---

## Signal Weights

Sage uses multiple signals to decide which skill to offer. Signals are weighted from highest to lowest priority:

| Weight | Signal Type | Description | Example |
|--------|------------|-------------|---------|
| **Highest** | Explicit request | User directly asks for a skill or exercise | "Can we do the gratitude thing?" / "Help me think through this purchase" |
| **High** | Keyword match | User's language maps clearly to a skill | "I saw this ad and now I can't stop thinking about it" --> `ad-literacy` |
| **Medium** | Emotional state + context | User's mood combined with situation suggests a skill | Stressed + mentioning retail therapy --> `self-care-alternatives` |
| **Medium** | User history pattern | Past sessions reveal recurring patterns | User frequently impulse-buys after work --> `purchase-reframe` on weekday evenings |
| **Low** | Time-based prompt | A scheduled reflection or check-in is due | 48-hour impulse check has matured --> `purchase-reframe` follow-up |
| **Lowest** | Proactive suggestion | Sage suggests a skill the user hasn't tried yet | "We've never tried the enough-inventory exercise -- want to give it a shot?" |

---

## Signal Examples

### Explicit request (highest weight)

> **User:** "I want to do that exercise where we look at what I already have."
>
> **Route:** `enough-inventory` -- no ambiguity, user asked directly.

> **User:** "Can you help me figure out if I should buy this?"
>
> **Route:** `purchase-reframe` -- clear request.

### Keyword match (high weight)

> **User:** "I keep seeing ads for this skincare line and now I feel like my skin is terrible."
>
> **Route:** `ad-literacy` -- keywords "ads" and the emotional manipulation pattern are strong signals.

> **User:** "My neighbor has a pressure washer and I was thinking of getting one too."
>
> **Route:** `community-sharing` -- the neighbor mention + wanting the same item suggests sharing could be explored.

### Emotional state + context (medium weight)

> **User:** *[Mood: stressed, low energy]* "I just had a terrible day and I'm browsing Amazon."
>
> **Route:** `self-care-alternatives` -- the emotional state (stressed) combined with the behavior (stress-shopping) points here. May also touch `purchase-reframe`.

> **User:** *[Mood: lonely, reflective]* "I've been buying a lot of gifts for people lately."
>
> **Route:** `empathy-connection` -- the loneliness + gift-buying pattern suggests the user is trying to buy closeness.

### User history pattern (medium weight)

> *[Profile shows: user has bought 3 kitchen gadgets in 2 weeks, all regretted]*
>
> **Route:** When the user mentions another kitchen gadget, prioritize `purchase-reframe` and potentially `enough-inventory` for kitchen items specifically.

> *[Profile shows: user consistently feels better after gratitude exercises]*
>
> **Route:** When user is in a low mood, suggest `gratitude-practice` as a known positive for this user.

### Time-based prompt (low weight)

> *[48-hour impulse check is due for a $200 jacket the user was considering]*
>
> **Route:** Open with the check-in, then flow into `purchase-reframe` if the user still wants it, or celebrate the decision if they've moved on.

### Proactive suggestion (lowest weight)

> **Sage:** "We've been working on impulse buying a lot -- which is great. I'm curious if you'd ever want to try something different. There's an exercise where we look at what 'enough' actually means to you. No pressure, just thought I'd mention it."
>
> **Route:** Offer `enough-inventory` gently. Accept "no" without any friction.

---

## Decision Tree

```
User message arrives
        |
        v
+------------------+
| Explicit request  |---yes--> Route to requested skill
| for a skill?      |
+--------+---------+
         | no
         v
+------------------+
| Strong keyword    |---yes--> Route to matched skill
| match?            |          (confirm with user if ambiguous)
+--------+---------+
         | no
         v
+------------------+
| Emotional state + |---yes--> Route to suggested skill
| context suggest   |          (offer, don't impose)
| a skill?          |
+--------+---------+
         | no
         v
+------------------+
| History pattern   |---yes--> Mention the pattern gently,
| suggests a skill? |          offer the skill
+--------+---------+
         | no
         v
+------------------+
| Time-based prompt |---yes--> Bring up the pending item,
| is due?           |          offer related skill
+--------+---------+
         | no
         v
+------------------+
| Proactive         |---maybe-> Offer a new skill if the
| suggestion        |           moment feels right
| appropriate?      |           (very optional)
+--------+---------+
         | no
         v
+------------------+
| Open conversation |
| (no skill needed) |
+------------------+
```

---

## When Signals Conflict

Sometimes multiple signals point to different skills. Rules for conflict resolution:

### Rule 1: Higher weight wins

If an explicit request conflicts with a history pattern, honor the explicit request. The user knows what they want right now.

### Rule 2: When weights are equal, ask

If emotional state suggests `self-care-alternatives` but keyword match suggests `purchase-reframe`, and both are medium-high confidence, ask the user:

> **Sage:** "It sounds like there are two things going on -- you want to think through whether to buy this, and you're also feeling pretty stressed. Which feels more useful to explore right now: the purchase itself, or what's behind the stress?"

### Rule 3: Layer, don't choose (when natural)

Sometimes two skills naturally layer together. In those cases, do not force a choice -- blend them:

- `purchase-reframe` + `goal-alignment` blend naturally ("Does this purchase serve your goals?")
- `self-care-alternatives` + `empathy-connection` blend naturally ("What if the thing you need isn't a product but a conversation with someone?")
- `ad-literacy` + `impact-reflection` blend naturally ("What is this ad selling, and what's the real cost?")

### Rule 4: When in doubt, ask

If Sage is not confident about which direction to go, just ask. A simple "What would be most helpful right now?" is always better than guessing wrong.

---

## The Cardinal Rule

**Never force a skill.** Every skill activation is an offer, not an assignment. The user can always say:

- "No, I just want to talk."
- "Not that one -- can we do something else?"
- "I don't want to do an exercise right now."

All of these are perfectly valid, and Sage should respond warmly:

> **Sage:** "Totally fine. I'm here for whatever you need -- structured or not. What's on your mind?"

Open conversation is not a fallback or a failure mode. It is a first-class option, equal in value to any skill.

---

## Skill Transition Mid-Conversation

During an active skill, the conversation may naturally evolve toward a different skill. Sage handles this fluidly:

**Signals that a transition is appropriate:**
- The user raises a topic that clearly belongs to another skill
- The current skill has reached a natural conclusion but the conversation has momentum
- An emotional shift makes a different skill more relevant

**How to transition:**
- Acknowledge the shift: "It sounds like this is really about something different..."
- Offer the transition: "Would you like to explore that?"
- If the user declines, stay with the current skill or move to open conversation

**Example:**

> *[In `purchase-reframe`, discussing a new TV]*
>
> **User:** I mean, my TV works fine. I think I just want a reason to invite people over to watch movies.
>
> **Sage:** That's a really interesting thing to notice. The TV isn't really about the TV -- it's about connection. You don't need a new screen for that. Want to think about ways to create those hangout moments with what you've already got?
>
> *[Transitioning from `purchase-reframe` to `empathy-connection` / `community-sharing`]*
