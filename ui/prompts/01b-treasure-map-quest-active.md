Design a treasure hunt map page for a cross-platform mobile application (iOS + Android). This shows the **quest in progress** state — the user has started today's quest, the quest bar is visible above the tab bar, and the floating quest card (bottom sheet) is expanded showing live progress.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") during active gameplay. The user has started today's quest. A quest bar above the tab bar shows "1/3 进行中" with a progress line. The user has tapped the quest bar, revealing a floating quest card showing detailed progress for all 3 quests. One quest is already completed (checked).

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. Visually unified across iOS and Android; platform-adaptive navigation behavior only.
Visual Tone: Soft and rounded — generous border radii (12-24px), gentle shadows, warm off-white surfaces.
Visual Strategy: Frosted-glass floating layers over full-bleed map. User's collar color as a personalization thread.

**Collar Color Personalization:**
5 collar color presets. In the design, use "Ocean Blue" (#3498DB) as the example collar color.
- Ocean Blue: #3498DB, lighter variant #5DADE2, glow rgba(52,152,219,0.4)

**Elements:**

Full-Screen Map (Apple Maps style — MUST be street-level detail):
- Fills entire screen behind all floating UI
- **Visual style: Apple Maps light theme** — clean, minimal cartography
- **Street-level zoom showing approximately 300-500m visible range** — this is a neighborhood treasure hunt, the map must show individual streets, building footprints, and park boundaries clearly
- Base color: very light warm grey (#F5F5F0 approximate)
- Parks and vegetation: soft muted green fills with subtle boundaries
- Roads: white/light grey fills, main roads slightly wider and brighter, side streets thinner and more grey
- Buildings: very subtle light grey footprints with thin outlines, no 3D extrusion
- Labels: small sans-serif text in dark grey for street names, slightly larger for landmarks/parks ("朝阳公园", "望京街道")
- Overall feel: quiet, recessive, low-contrast — lets chest markers and quest UI pop visually
- User position marker: 40×40 blue gradient circle with 🐕 inside, pulsing ring
- Status bar and marquee at top.

Treasure Chest Markers (same as main map, scatter 7):
- Mix of points chests (📦), merchant chests (🎁), one openable within 50m with bounce + glow
- Show variety of states: far, openable, claimed

Quest Bar (above tab bar):
- Position: directly above tab bar, 16px horizontal margin, 12px bottom gap
- Size: full width minus margins, 44px height
- Style: white 90% opacity, backdrop-filter blur 12px, border-radius 12px, shadow 0 2px 12px rgba(0,0,0,0.08). On lower-end devices: white 95% without blur.
- Bottom progress line: 3px height, collar-color fill, width 33% (1/3 complete), smooth animated
- Left: 🐾 icon in collar color (16px)
- Text: "1/3 进行中" (14px, weight 600, #333)
- Right-aligned hint: "最近: 东北230m" (13px, #999)

Quest Card (Floating Bottom Sheet — expanded, hero element of this state):
- Trigger: quest bar tapped (shown in expanded state)
- Position: above tab bar area, 24px horizontal margin (centered, ~85% screen width), 12px above tab bar
- All four corners rounded: border-radius 16px
- White background, shadow 0 8px 32px rgba(0,0,0,0.12)
- Drag handle: 36×4px, #F0F0F0, centered, 8px from top
- Semi-transparent overlay behind: rgba(0,0,0,0.3) covering map area

Card Content:
- Header row: "今日寻宝任务" (16px, weight 700, #333) left, "1/3" (14px, weight 700, collar color) right
- 16px gap below header
- 3 quest items, each 48px height:
  - Checkbox: 20×20 rounded square
    - Quest 1 (complete): collar-color fill + white ✓, name "开启 3 个宝箱" with strikethrough #999
    - Quest 2 (in progress): 2px border #CCC, name "遛狗满 15 分钟" in #333
    - Quest 3 (not started): 2px border #CCC, name "探索商家宝箱" in #333
  - Live progress right of name: 13px, #999 (e.g., "3/3 ✓", "8:32/15:00", "0/1")
  - Reward label right-aligned: "+20 积分" (13px, #FFB800) or "🎯 任务宝箱" (13px, collar color)
  - Separated by 0.5px #F5F5F5 divider
- No "出发" button (quest already active)
- Close: tap overlay or swipe card down

Right-Side Floating Buttons:
- Locate Button: 44×44 circle, white background, 📍 icon
- Activity Button (conditional): 44×44 circle, 🎉 icon, collar-color ring
- Filter Button (left side): capsule, "⚙️ 筛选"

Tab Bar (fixed bottom):
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的

**States:**
- Default (shown): Quest in progress, quest bar visible, quest card expanded with 1/3 quests complete
- Quest bar only (card collapsed): Quest bar showing "1/3 进行中", no overlay

**Style:**
- Design system: PawQuest custom branded system
- Map style: Apple Maps light theme — street-level, 300-500m visible range
- Primary accent: #FFB800 (gold), Commerce accent: #FF3B30 (red)
- Personalization accent: collar color (#3498DB Ocean Blue)
- Border radius: 12px (quest bar), 16px (quest card, all corners)
- Frosted glass: quest bar uses backdrop-filter blur
- Shadows: sm (buttons), md (quest bar), lg (quest card)
- Typography: PingFang SC (iOS) / Noto Sans SC (Android), DIN Alternate for numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- Map SDK: AMap (高德地图), styled to resemble Apple Maps light theme at street level
- All text in Chinese (Simplified)
- Quest card is a floating card (not edge-to-edge bottom sheet) with 24px horizontal margin and all-corner rounding
