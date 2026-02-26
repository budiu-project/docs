Design a treasure hunt map page for a cross-platform mobile application (iOS + Android). This shows the **quest summary card expanded** — the user has tapped the "Start Treasure Hunt" button and it has morphed into a frosted-glass quest summary card at map center.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") showing the moment after the user taps the center "Start" button. The button has transformed into a floating quest summary card displaying today's 3 quests, with a "出发" (Go) button at the bottom. The map and chests remain visible behind the card.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. Visually unified across iOS and Android; platform-adaptive navigation behavior only.
Visual Tone: Soft and rounded — generous border radii (12-24px), gentle shadows, warm off-white surfaces.
Visual Strategy: Frosted-glass floating layers over full-bleed map. User's collar color as a personalization thread.

**Collar Color Personalization:**
5 collar color presets. In the design, use "Ocean Blue" (#3498DB) as the example collar color.
- Ocean Blue: #3498DB, lighter variant #5DADE2, glow rgba(52,152,219,0.4)

**Elements:**

Full-Screen Map (Apple Maps style — MUST be street-level detail):
- Fills entire screen behind all floating UI, visible behind the frosted-glass card
- **Visual style: Apple Maps light theme** — clean, minimal cartography
- **Street-level zoom showing approximately 300-500m visible range** — this is a neighborhood treasure hunt, the map must show individual streets, building footprints, and park boundaries clearly
- Base color: very light warm grey (#F5F5F0 approximate)
- Parks and vegetation: soft muted green fills with subtle boundaries
- Roads: white/light grey fills, main roads slightly wider and brighter, side streets thinner and more grey
- Buildings: very subtle light grey footprints with thin outlines, no 3D extrusion
- Labels: small sans-serif text in dark grey for street names, slightly larger for landmarks/parks ("朝阳公园", "望京街道")
- Overall feel: quiet, recessive, low-contrast — lets the quest card and chest markers pop visually
- User position marker: 40×40 blue gradient circle with 🐕 inside, pulsing ring
- Treasure chest markers scattered on map (📦 and 🎁 at various distances)
- Status bar and marquee remain visible at top. Tab bar visible at bottom. No quest bar in this state.

Quest Summary Card (center of map — hero element of this state):
- Position: vertically and horizontally centered on map viewport
- Size: 75% of screen width (~281px on 375px viewport), height auto based on content
- Shape: rounded rectangle, border-radius 20px
- Background: white 85% opacity, backdrop-filter blur 16px saturate 180%. On lower-end devices: white 92% opacity without blur.
- Shadow: 0 8px 32px rgba(0,0,0,0.12), 0 0 0 0.5px rgba(255,255,255,0.5) inset
- No dark overlay behind card (map remains interactive-feeling, frosted glass provides sufficient visual separation)

Card Content:
- Top padding: 20px, side padding: 20px, bottom padding: 16px
- Header row: 🐾 icon (16px, collar color) + "今日寻宝任务" (15px, weight 700, #333), right-aligned "0/3" (15px, weight 700, collar color)
- Divider: 12px gap, then 0.5px line #F0F0F0
- 3 quest summary rows, each ~36px height, 8px vertical gap between:
  - Left: 12px circle, 2px collar-color stroke, hollow (not yet started)
  - Quest name: 14px, weight 500, #333 (e.g., "开启 3 个宝箱", "遛狗满 15 分钟", "探索商家宝箱")
  - Right-aligned reward: 13px, #999 (e.g., "+20分", "+15分", "🎯")
  - Rows separated by 0.5px #F5F5F5 divider
- 16px gap after last quest row
- "出发" button:
  - Full width within card padding
  - Height: 40px, border-radius 20px
  - Background: collar-color gradient (lighter → standard, e.g., #5DADE2 → #3498DB)
  - Text: "出发" (15px, weight 700, white, centered)
  - Shadow: 0 4px 14px with collar-color at 30% opacity
  - Press feedback: scale(0.96)

Interaction note (for design context, not visual):
- Tapping outside the card dismisses it (card morphs back into the round button)
- Tapping "出发" starts the quest (card collapses, quest bar slides in from bottom)

**States:**
- Default (shown): Quest summary card expanded at center, map and chests visible behind frosted glass
- This is a transient state — user either taps "出发" to start or taps outside to dismiss

**Style:**
- Design system: PawQuest custom branded system
- Map style: Apple Maps light theme — street-level, 300-500m visible range
- Primary accent: #FFB800 (gold), Commerce accent: #FF3B30 (red)
- Personalization accent: collar color (#3498DB Ocean Blue)
- Border radius: 20px (quest summary card), 20px (出发 button)
- Frosted glass: white 85% + backdrop-filter blur 16px saturate 180%
- Typography: PingFang SC (iOS) / Noto Sans SC (Android), DIN Alternate for numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- Map SDK: AMap (高德地图), styled to resemble Apple Maps light theme at street level
- All text in Chinese (Simplified)
