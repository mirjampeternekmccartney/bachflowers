# PRD — Bach Flower Essence Guide (working title: "Find Your Essence")

Status: Draft v0.1 · 2026-11-04 · Owner: Lemongrass Marketing

## 1. Summary
A website that works as a gamified guide to choosing from the 38 Bach flower essences. It is based on the guide at healingherbs.co.uk and on how people feel (their symptoms). It teaches complete beginners how the remedies are organised (the Twelve Healers, the Seven Helpers and the Second Nineteen) while they play.

## 2. Problem and opportunity
- Newcomers find 38 remedies overwhelming. The names are unfamiliar and the descriptions are long.
- Existing guides are reference lists, not experiences. People give up or pick at random.
- A playful, guided path builds confidence, encourages return visits and gives Lemongrass a shareable, brandable asset.

## 3. Goals
1. A beginner understands what the three groups are and how to use them after one session.
2. A user gets a shortlist of essences matched to how they feel, with a clear "why".
3. The experience is fun enough that most users finish it and many replay it.

Non-goals: medical diagnosis, treatment claims, e-commerce checkout (v1), user accounts (v1).

## 4. Target users
- **Curious newcomer** (primary): has heard of Rescue Remedy, knows nothing else.
- **Gift/self-care browser**: wants quick guidance for themselves or someone else.
- **Practitioner/student** (secondary): wants a revision and teaching tool.

## 5. Content model
Source: healingherbs.co.uk guide. Paraphrase and credit; do not copy verbatim. Verify every remedy's keywords against the source before launch.

| Group | Remedies | Plain-English idea |
|---|---|---|
| Twelve Healers | Agrimony, Centaury, Cerato, Chicory, Clematis, Gentian, Impatiens, Mimulus, Rock Rose, Scleranthus, Vervain, Water Violet | Personality types; the most common starting point (verified vs healingherbs.co.uk) |
| Seven Helpers | Gorse, Heather, Oak, Olive, Rock Water, Vine, Wild Oat | Support essences for long-term emotional states (verified vs healingherbs.co.uk) |
| Second Nineteen | Aspen, Beech, Cherry Plum, Chestnut Bud, Crab Apple, Elm, Holly, Honeysuckle, Hornbeam, Larch, Mustard, Pine, Red Chestnut, Star of Bethlehem, Sweet Chestnut, Walnut, White Chestnut, Wild Rose, Willow | Reactions to events and states of mind, often temporary |
| Rescue Remedy (bonus) | Combination of 5 essences | Taught as the "first-aid" intro, not one of the 38 |

Each remedy record (one data file, e.g. `remedies.json`): id, name, group, one-line plain summary, feelings/symptom tags, "when to think of it" example, negative state, positive outcome, illustration/icon, source link.

Also tag each remedy with the classic seven emotional families (fear, uncertainty, insufficient interest in present circumstances, loneliness, over-sensitivity, despondency, over-care for others) to power the matching.

## 6. Core experience
### 6.1 Learn: "Meet the three groups" (onboarding, about 2 min)
Short, illustrated, interactive intro. Each group is a "party role" the player unlocks:
- Healers = your core character
- Helpers = your support crew
- Second Nineteen = the situational toolkit
Includes how to use essences in plain terms (pick a few, no overdose, general dosing as stated in the source) and the "not medical advice" note.

### 6.2 Play: "How are you feeling?" (main game)
1. Player picks the feelings or symptoms they relate to (tap cards, e.g. "I can't switch my mind off", "I feel drained", "I'm scared but can't say why").
2. A guided question flow narrows the options, with short follow-ups.
3. The game scores remedies and reveals a shortlist (maximum 5) as "essence cards", each with a plain-English reason.
4. Player builds a personal "blend" (cap of 5, per healingherbs.co.uk; 5 Flower counts as one essence) and can save or share it.

### 6.3 Games and challenges
- **Match the Remedy:** pair feelings with essences (flashcard-style).
- **Which Group?** Sort essences into Healers, Helpers or Second Nineteen.
- **Scenario Quest:** short stories where the player picks the best essence; instant feedback and a fun fact.
- Progress: XP, collectible essence cards (38 plus the bonus), group badges, daily 3-question challenge.

### 6.4 Results and next steps
- Personal summary page (printable or shareable image).
- Link out to healingherbs.co.uk for the full guide and purchase (outbound, no checkout in v1).
- Optional email capture for the blend plus tips (Lemongrass lead-gen; needs consent and GDPR wording).

## 7. Functional requirements
| ID | Requirement | Priority |
|---|---|---|
| F1 | Intro explains the three groups simply | Must |
| F2 | Symptom/feeling selector with at least 60 curated feeling statements mapped to remedies | Must |
| F3 | Matching engine with weighted scoring and a transparent "why" per result | Must |
| F4 | Remedy cards for all 38 (plus Rescue Remedy) | Must |
| F5 | Match, sort and scenario mini-games | Must |
| F6 | XP, badges and a card collection (stored locally) | Should |
| F7 | Shareable or printable result | Should |
| F8 | Email capture with consent | Could |
| F9 | Multi-language support | Won't (v1) |

Matching logic: each feeling statement carries weights per remedy. Score = sum of the weights of the selected statements. Show the top matches, flag close ties and let the user read the cards and decide.

## 8. Non-functional requirements
- Mobile-first, responsive, works offline-capable as a static site.
- Fast: LCP under 2.5 s on 4G.
- Accessible: WCAG 2.2 AA, keyboard navigable, no colour-only meaning, reduced-motion option.
- Plain language: reading age about 12; no jargon without a tooltip.
- Privacy: no tracking without consent; progress stored locally.
- Tech suggestion: static site (HTML/CSS/JS or a light framework), content in JSON, hosted on any static host.

## 9. Content and compliance guardrails
- Prominent disclaimer: essences are complementary, not a substitute for medical care; see a doctor for physical or mental health concerns.
- No claims to diagnose, treat or cure. Use wording like "people traditionally choose…".
- Crisis safeguard: if a user selects self-harm or severe distress statements, show support resources rather than a remedy-only result.
- Attribution: credit healingherbs.co.uk; confirm permission or licensing for use of its guide as the source before launch.

## 10. Success metrics
- Intro completion rate of at least 70%.
- At least 50% of players complete the main flow and see a result.
- Quiz accuracy improves between the first and third mini-game round (learning signal).
- Return visitors of at least 20% within 30 days.
- Share/print rate and outbound clicks to the source guide.

## 11. Milestones
1. **Content:** extract and paraphrase all 38 remedies, tags and weights; review for accuracy.
2. **Design:** brand look and feel, card art style, wireframes.
3. **Build MVP:** intro, feelings flow, results, remedy cards.
4. **Add games and progression:** match, sort, scenario, badges.
5. **QA and accessibility:** content review and user testing with 5 to 8 beginners.
6. **Launch and measure.**

## 12. Risks and open questions
- Permission to use healingherbs.co.uk content; otherwise, build from public-domain Bach descriptions.
- Content accuracy; ideally reviewed by a qualified practitioner.
- Tone: playful without trivialising health. Needs a sign-off on the voice.
- Open: brand name and visual style? Email capture in v1? Include Rescue Remedy as a core feature? Embed on an existing Lemongrass or client site, or standalone?
