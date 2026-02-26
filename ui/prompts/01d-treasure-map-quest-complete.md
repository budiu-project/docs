Design a treasure hunt map page for a cross-platform mobile application (iOS + Android). This shows the **all quests completed** state — all 3 daily quests are done, the quest bar glows with a collar-color ring, and a task reward chest (🎯) has appeared on the map near the user.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") at the daily quest completion milestone. The user has finished all 3 quests. The quest bar displays a celebratory state with collar-color glow. A special task reward chest (🎯) has spawned nearby on the map, beckoning the user to collect the final reward.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. Visually unified across iOS and Android.
Visual Strategy: This is the "achievement moment" — the quest bar and task chest should feel special and rewarding through collar-color glow effects, but the celebration stays contained (no confetti or full-screen effects).

**Collar Color Personalization:**
In the design, use "Ocean Blue" (#3498DB) as the example collar color.
- Ocean Blue: #3498DB, lighter #5DADE2, glow rgba(52,152,219,0.4), particles #6BC5E8/#4A90D9

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
- Overall feel: quiet, recessive, low-contrast — lets task chest glow and quest bar celebration pop visually
- User position marker: 40×40 blue gradient circle with 🐕 inside, pulsing ring
- Status bar and marquee at top.

Treasure Chest Markers:
- Regular chests remain on map (mix of 📦 and 🎁 in various states)
- **Task Reward Chest (hero element):** 🎯 emoji 34px, positioned near the user (within 50m on map)
  - Outer glow ring: collar-color, pulsing scale 1→1.15 over 1.5s (same spec as rare chest but collar-colored)
  - Label below: "任务奖励" (12px, collar color, weight 600, white 90% background pill)
  - Bounce animation: translateY -4px, 0.6s ease-in-out infinite
  - This chest is visually the most prominent marker on the map

Quest Bar (above tab bar — celebratory state):
- Position: directly above tab bar, 16px horizontal margin, 12px bottom gap
- Size: full width minus margins, 44px height
- Style: white 90% opacity, backdrop-filter blur 12px, border-radius 12px
- Bottom progress line: 3px height, collar-color fill, width 100% (all complete)
- Left: 🎯 icon (16px)
- Text: "任务完成！领取奖励宝箱" (14px, weight 700, collar color)
- **Outer glow ring:** 2px collar-color stroke around entire bar, pulsing opacity 50%→100% over 1.5s (same ring style as activity button)
- Shadow enhanced: 0 2px 12px rgba(0,0,0,0.08), plus collar-color glow 0 0 16px collar-glow at 40% opacity

Toast notification (floating above quest bar):
- "🎉 今日任务全部完成！" toast
- Position: centered horizontally, ~100px above quest bar
- Style: dark pill (rgba(0,0,0,0.75)), white text 14px, border-radius 20px, padding 10px 20px
- Auto-dismiss after 3s with fade-out

Right-Side Floating Buttons:
- Locate Button: 44×44 circle, white, 📍 icon
- Activity Button (conditional): 44×44 circle, 🎉 icon, collar-color ring
- Filter Button (left side): capsule, "⚙️ 筛选"

Tab Bar (fixed bottom):
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的

**States:**
- Default (shown): All quests complete, quest bar glowing, task chest visible on map with collar-color glow, toast visible
- After toast dismisses: Same but without toast, quest bar continues to glow
- After collecting task chest: Quest bar returns to normal "3/3 完成" state without glow (task chest removed from map)

**Style:**
- Design system: PawQuest custom branded system
- Map style: Apple Maps light theme — street-level, 300-500m visible range
- Primary accent: #FFB800 (gold)
- Personalization accent: collar color (#3498DB Ocean Blue) — dominant in this state, used on quest bar text, quest bar glow ring, task chest glow ring, and task chest label
- Border radius: 12px (quest bar), 20px (toast pill)
- Frosted glass: quest bar backdrop-filter blur
- Glow rings: collar-color pulsing opacity on quest bar and task chest marker
- Typography: PingFang SC (iOS) / Noto Sans SC (Android)

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- Map SDK: AMap (高德地图), styled to resemble Apple Maps light theme at street level
- All text in Chinese (Simplified)
- Medium haptic feedback triggered when quest completion state is reached (platform-adaptive)
- Task chest spawns within 50m of user's current location
