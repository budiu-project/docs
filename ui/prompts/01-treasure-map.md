Design a treasure hunt map page for a cross-platform mobile application (iOS + Android). This is the **default state with daily quest not yet started** — the "Start Treasure Hunt" button is prominently displayed at map center.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") in its initial daily state. User has not started today's quest yet. The map shows nearby treasure chests, and a large "Start Treasure Hunt" button with a collar-color glow ring sits at the center, inviting the user to begin.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. Game-inspired treasure hunt mechanics wrapped in a warm, approachable visual language that feels like a daily lifestyle companion rather than a mobile game. Visually unified across iOS and Android; platform-adaptive navigation behavior only.
Mood: Warm, Discovery, Casual Delight, Outdoor Vitality.
Visual Tone: Soft and rounded — generous border radii (12-24px), gentle shadows, warm off-white surfaces. Approachable without being cartoonish, similar in restraint to Xiaohongshu or Keep.
Visual Strategy: Gold (#FFB800) as signature accent for treasure/points. Frosted-glass floating layers over full-bleed map (with graceful degradation on lower-end devices). Emoji-based map markers for instant recognition. Micro-animations serve comprehension, not decoration. User's collar color as a personalization thread across interactive elements.

**Collar Color Personalization:**
The user owns a physical smart dog collar. Its color is reflected in UI elements as a personal accent. 5 collar color presets:
- Classic Red: #E74C3C, glow rgba(231,76,60,0.4), particles #FF6B6B/#FF3B30
- Ocean Blue: #3498DB, glow rgba(52,152,219,0.4), particles #6BC5E8/#4A90D9
- Forest Green: #27AE60, glow rgba(39,174,96,0.4), particles #6FCF97/#34C759
- Premium Gold: #F1C40F, glow rgba(241,196,15,0.4), particles #FFD700/#FFB800
- Midnight Black: #2C3E50, glow rgba(44,62,80,0.3), particles #BDC3C7/#ECF0F1 (silver-white)
Default (no collar bound): falls back to #FFB800 (gold).
In the design, use "Ocean Blue" (#3498DB) as the example collar color.

**Elements:**

Floating Status Bar (over map):
- Position: below system status bar safe area, 16px horizontal margin
- Size: full width minus margins, 44px height
- Style: white 80% opacity, backdrop-filter blur 12px, border-radius 12px, shadow 0 2px 12px rgba(0,0,0,0.08). On lower-end devices: white 92% opacity without blur.
- Left section: gold coin icon (16×16) + text "今日 +85 分" (14px, weight 500, #333)
- Center: "3/10" chest progress (14px, weight 500, #666, tabular-nums)
- Right section: coupon icon 🎫 (22px) in 44×44 tap area, red notification dot (8×8) at top-right corner

World Message Marquee:
- Position: directly below status bar, 16px horizontal margin
- Size: 28px height, border-radius 8px
- Style: semi-transparent dark background rgba(0,0,0,0.5), backdrop-filter blur 8px. On lower-end devices: rgba(0,0,0,0.6) without blur.
- Left: fixed 🎉 icon (not scrolling), 6px gap to scrolling text
- Text: 13px white, single line, scrolls right-to-left at ~50px/s
- Sample messages: "恭喜小明开出稀有宝箱！", "汪汪 领取了萌宠屋优惠券", "Lucky 完成了今日全部任务 🎯"
- 2-second pause between messages
- Hidden when no messages (no space reserved)

Full-Screen Map (Apple Maps style):
- Fills entire screen behind all floating UI
- Visual style: Apple Maps light theme — clean, minimal cartography
- Street-level zoom showing approximately 300-500m visible range
- Base color: very light warm grey (#F5F5F0 approximate)
- Parks and vegetation: soft muted green fills with subtle boundaries
- Roads: white/light grey fills, main roads slightly wider and brighter, side streets thinner and more grey
- Buildings: very subtle light grey footprints with thin outlines, no 3D extrusion
- Labels: small sans-serif text in dark grey for street names, slightly larger for landmarks/parks
- Overall feel: quiet, recessive, low-contrast — lets treasure chest markers and center button pop visually
- User position marker: 40×40 circle with gradient (#4A90D9 → #357ABD), dog emoji 🐕 inside, pulsing ring (80×80, rgba(74,144,217,0.15), 2s ease-out infinite)

Treasure Chest Markers (scatter 7 across map):
- Points chest (far): 📦 emoji 28px, distance pill below ("230m" — 11px #666, white 80% background, rounded pill)
- Points chest (openable, within 50m): 📦 28px, bounce animation (translateY -4px, 0.6s ease-in-out infinite), brightened with gold glow (drop-shadow 0 2px 8px rgba(255,184,0,0.5) + brightness 1.15), label shows "可开启" (12px, #34C759, bold, white 90% background)
- Merchant chest (far): 🎁 34px (larger than points), distance pill
- Merchant chest (openable): 🎁 34px, bounce + glow, "可开启" label
- Rare chest (openable): 👑 34px, purple glow ring (radial-gradient rgba(175,82,222,0.4), pulsing scale 1→1.15 over 1.5s), bounce, "可开启" label
- Merchant chest (claimed): 🎁 34px, grayscale + 50% opacity, green checkmark circle at bottom-right, label "已领取" (#999)
- Points chest (very far): 📦 28px, "520m" label

**Start Treasure Hunt Button (center of map — hero element of this state):**
- Position: exact center of the map viewport, vertically and horizontally centered
- Shape: circle, 80px diameter
- Background: collar-color gradient (lighter → standard, e.g., #5DADE2 → #3498DB for ocean blue)
- Icon: white 🐾 (32px) centered inside
- Label below button: "开始寻宝" (13px, white, weight 700), 8px gap below circle
- Shadow: 0 4px 20px with collar-color glow (e.g., rgba(52,152,219,0.4))
- Outer glow ring: 3px wide, 6px gap from button edge, collar-color, pulsing opacity 50%→100% over 1.5s (same animation spec as rare chest glow)
- Idle animation: glow ring pulses continuously + button floats gently up/down (translateY ±3px, 3s ease-in-out infinite)
- Press feedback: scale(0.92), glow ring pauses
- This button is the primary visual focal point of the page in this state

Right-Side Floating Buttons (stacked vertically, right edge):
- Locate Button: 44×44 circle, white background, 📍 icon, shadow
- Activity Button (conditional): 44×44 circle, white background, 🎉 icon, collar-color pulsing ring, red dot for new campaigns
- Filter Button (left side): capsule shape, 36px height, "⚙️ 筛选"

Tab Bar (fixed bottom):
- Height: 56px + platform safe area
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的

**Important:** In this state, there is NO quest bar above the tab bar. The quest bar only appears after the user starts the quest. The "Start Treasure Hunt" button at map center is the sole entry point for beginning the daily quest.

**States:**
- Default (shown): Map loaded, chests scattered, Start Treasure Hunt button at center with glow ring pulsing, marquee scrolling
- Loading: Map loading skeleton, button not yet visible
- Empty — no chests: Centered illustration + "附近暂无宝箱，换个地方遛遛看", Start button still visible above illustration
- Error — weak GPS: Alert bar persists: "GPS 信号弱，请移至空旷处"
- Error — network: Alert bar + "重试" button
- Error — location denied: Full-screen overlay with "去设置" button

**Style:**
- Design system: PawQuest custom branded system — warm gamification, soft rounded aesthetics
- Map style: Apple Maps light theme
- Primary accent: #FFB800 (gold), Commerce accent: #FF3B30 (red)
- Personalization accent: collar color (#3498DB Ocean Blue in this design)
- Border radius: 8px (tags), 12px (status bar, dropdown), 16px (cards), 20px (quest summary card), 24px (large buttons)
- Frosted glass: backdrop-filter blur on floating elements, graceful degradation
- Shadows: 4-level system — sm, md, lg, colored
- Glow rings: collar-color pulsing opacity, used on start button, activity button, task chest
- Typography: PingFang SC (iOS) / Noto Sans SC (Android) for text, DIN Alternate for display numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- Map SDK: AMap (高德地图), styled to resemble Apple Maps light theme
- All text in Chinese (Simplified)
- Emoji-based iconography for map markers and UI elements
- Back navigation: left swipe gesture (iOS) / system back button (Android)
