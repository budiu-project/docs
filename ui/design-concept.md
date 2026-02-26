# Design Concept

## Design Philosophy

**Warm Gamification** — Game-inspired treasure hunt mechanics to motivate dog walking, wrapped in a warm, approachable visual language that feels like a daily lifestyle companion rather than a mobile game.

This fits the product because the core loop (walk dog → find chest → get reward) needs to feel rewarding without being addictive or childish. The target users are pet owners who want a pleasant walking experience, not hardcore gamers.

## Mood & Atmosphere

**Keywords:** Warm, Discovery, Casual Delight, Outdoor Vitality

The app should evoke the feeling of a sunny afternoon walk — discovering small surprises along the way. Every interaction (opening a chest, earning points, receiving a coupon) should deliver a brief moment of delight without demanding attention.

## Visual Strategy

- **Color Psychology:** Gold (#FFB800) as the signature accent — conveys "treasure found" excitement. Red (#FF3B30) reserved for merchant commerce (coupons, CTAs). Warm off-white (#F7F6F3) background grounds the experience in calm daily life. Purple (#AF52DE) used sparingly for rare/premium moments.
- **Typography & Hierarchy:** iOS-native sizing hierarchy. Large bold numbers for key metrics (points balance, coupon value). Restrained secondary text. Tabular-nums for all numerical displays.
- **Spacing & Layout:** Card-based composition with generous padding. Map page uses full-bleed map with frosted-glass floating layers. Sub-pages follow standard iOS list/card patterns. 16px base margin, 8px spacing grid.
- **Iconography:** Emoji-based chest markers (📦🎁👑) on the map for instant recognition at small sizes. Standard system icons elsewhere.

## Interaction Principles

- **Micro-feedback, not spectacle:** Subtle bounce when a chest becomes openable, brief particle burst on open, smooth slide transitions between pages. Animations serve comprehension (state change feedback), not decoration.
- **Progressive disclosure:** Map shows minimal chrome; details emerge through bottom sheets and sub-pages. No information overload on the primary exploration surface.
- **Tactile confidence:** Press feedback (scale 0.97-0.98) on tappable cards and buttons. Frosted glass + shadow layering creates clear depth hierarchy.
