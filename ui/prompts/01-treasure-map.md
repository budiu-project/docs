Design a treasure hunt map page for a cross-platform mobile application (iOS + Android).

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") where users explore a full-screen map, discover nearby treasure chests, walk into range (50m), and open them for rewards. Also hosts a daily quest system, world message marquee, and campaign entry point. This is the core gameplay loop.

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
- Campaign announcement messages are tappable (navigate to campaign page)

Alert Bar (conditional, slides in from top):
- Position: directly below marquee (or below status bar if marquee hidden), 16px horizontal margin
- Size: 36px height, border-radius 8px
- Types: Warning (#FFF3CD text #856404), Error (#F8D7DA text #721c24), Info (#D1ECF1 text #0c5460)
- Animation: slide down 0.2s ease-out, info type auto-dismiss after 3s
- Sample text: "这个宝箱刚被领走了" (info type)

Full-Screen Map (Apple Maps style):
- Fills entire screen behind all floating UI
- **Visual style: Apple Maps light theme** — clean, minimal cartography
- Street-level zoom showing approximately 300-500m visible range
- Base color: very light warm grey (#F5F5F0 approximate)
- Parks and vegetation: soft muted green fills with subtle boundaries
- Roads: white/light grey fills, main roads slightly wider and brighter, side streets thinner and more grey
- Buildings: very subtle light grey footprints with thin outlines, no 3D extrusion
- Water features (if any): soft pale blue
- Labels: small sans-serif text in dark grey for street names, slightly larger for landmarks/parks ("朝阳公园", "望京街道", "东风北桥")
- Overall feel: quiet, recessive, low-contrast — lets treasure chest markers pop visually
- User position marker: 40×40 circle with gradient (#4A90D9 → #357ABD), dog emoji 🐕 inside, pulsing ring (80×80, rgba(74,144,217,0.15), 2s ease-out infinite)

Treasure Chest Markers (scatter 7 across map + 1 task chest):
- Points chest (far): 📦 emoji 28px, distance pill below ("230m" — 11px #666, white 80% background, rounded pill)
- Points chest (openable, within 50m): 📦 28px, bounce animation (translateY -4px, 0.6s ease-in-out infinite), brightened with gold glow (drop-shadow 0 2px 8px rgba(255,184,0,0.5) + brightness 1.15), label shows "可开启" (12px, #34C759, bold, white 90% background)
- Merchant chest (far): 🎁 34px (larger than points), distance pill
- Merchant chest (openable): 🎁 34px, bounce + glow, "可开启" label
- Rare chest (openable): 👑 34px, purple glow ring (radial-gradient rgba(175,82,222,0.4), pulsing scale 1→1.15 over 1.5s), bounce, "可开启" label
- Merchant chest (claimed): 🎁 34px, grayscale + 50% opacity, green checkmark circle (16×16, #34C759 background, white ✓) at bottom-right, label "已领取" (#999)
- Points chest (very far): 📦 28px, "520m" label
- Task chest (unlocked after completing all daily quests): 🎯 34px, collar-color glow ring (same pulsing style as rare chest but using collar color), label "任务奖励" (12px, collar color)
- Entrance animation: chests animate in with staggered entrance (scale 0→1 + translateY, 0.4s each, 80ms delay between)

Right-Side Floating Buttons (stacked vertically, right edge):
- Position: right side, 16px from right edge, above tab bar area
- Stack order (bottom to top): Locate button → Activity button (conditional)
- 12px vertical gap between buttons

- Activity Button (conditionally visible when campaigns are active):
  - 44×44 circle, white background, shadow 0 2px 12px rgba(0,0,0,0.08)
  - 🎉 icon (20px) centered
  - Outer ring: 2px collar-color stroke, pulsing opacity 50%→100% over 1.5s
  - Red notification dot (8×8) at top-right when new campaign unseen
  - Entrance animation: slides in from right (0.3s) + subtle bounce (0.2s) when new campaign starts
  - Hidden entirely when no active campaigns
  - Tap: opens campaign H5 page in WebView with nav bar

- Locate Button:
  - 44×44 circle, white background, shadow 0 2px 12px rgba(0,0,0,0.08)
  - 📍 icon (20px) centered
  - Press feedback: collar-color ripple expands outward from center (0.4s)
  - Tap: re-centers map on user's current location

Left-Side Bottom Controls:
- Filter Button:
  - Position: left side, 16px from left edge, same vertical level as locate button
  - Capsule shape, 36px height, 14px horizontal padding
  - White background, shadow 0 2px 12px rgba(0,0,0,0.08)
  - ⚙️ icon + "筛选" text (13px, weight 500, #333)
  - No collar-color treatment (utility button, kept neutral)

Filter Dropdown (expanded state):
- Position: above filter button
- White background, border-radius 12px, shadow 0 4px 20px rgba(0,0,0,0.12)
- 3 options stacked: "全部" (active — #E5A600, bold), "📦 积分宝箱", "🎁 商家宝箱"
- Each option: 12px vertical padding, 20px horizontal padding, 14px text, separated by 1px #F5F5F5 border

Quest Bar (always visible, above tab bar):
- Position: directly above tab bar, 16px horizontal margin, 12px bottom gap from tab bar
- Size: full width minus margins, 44px height
- Style: white 90% opacity, backdrop-filter blur 12px, border-radius 12px, shadow 0 2px 12px rgba(0,0,0,0.08). On lower-end devices: white 95% opacity without blur.
- Bottom progress line: 3px height at very bottom of bar, collar-color fill, width proportional to quest completion (e.g., 33% = 1/3 complete), smooth transition on change (0.3s ease)

- State A — Not started:
  - Left: 🐾 icon in collar color (16px)
  - Text: "今日寻宝任务 ▸" (14px, weight 500, #333)
  - Tap: expands quest card (bottom sheet)

- State B — In progress:
  - Left: 🐾 icon in collar color
  - Text: "1/3 进行中" (14px, weight 600, #333)
  - Right-aligned hint: "最近: 东北230m" (13px, #999)
  - Bottom progress bar fills proportionally
  - Tap: expands quest card

- State C — All complete:
  - Left: 🎯 icon
  - Text: "任务完成！领取奖励宝箱" (14px, weight 700, collar color)
  - Outer glow: collar-color pulsing ring around entire bar (same style as activity button ring)
  - Tap: spawns task chest on map near user (within 50m)

Quest Card (Bottom Sheet):
- Trigger: tap quest bar
- Slides up from bottom, ~33% screen height
- White background, top border-radius 16px, drag handle (36×4px, #F0F0F0, centered)
- Semi-transparent overlay behind (rgba(0,0,0,0.3))

- Header row: "今日寻宝任务" (16px, weight 700, #333) left-aligned, "1/3" (14px, collar color) right-aligned
- 3 quest items, each 48px height:
  - Checkbox: 20×20 rounded square, unchecked = 2px border #CCC, checked = collar-color fill + white ✓
  - Quest name: 15px, #333 (e.g., "开启 3 个宝箱", "遛狗满 15 分钟", "探索商家宝箱")
  - Live progress: 13px, #999 (e.g., "2/3", "8:32/15:00", "0/1")
  - Reward label right-aligned: "+20 积分" (13px, #FFB800) or 🎯 icon for task chest reward
- "出发" button (only when not started):
  - Full width, 44px height, border-radius 24px
  - Background: collar-color gradient (lighter → standard, e.g., #5DADE2 → #3498DB for ocean blue)
  - Text: "出发" (15px, weight 700, white)
  - Shadow: 0 4px 12px with collar-color at 30% opacity
- Close: tap overlay or swipe down

Points Reward Bottom Sheet:
- Slides up from bottom, ~25% screen height
- White background, top border-radius 16px, drag handle
- Content centered: gold coin 🪙 (48px), "+15 积分" (32px, weight 900, #FFB800, DIN Alternate font), "当前共 1,295 积分" (14px, #999)
- Semi-transparent overlay behind

Merchant Coupon Reward Bottom Sheet:
- Slides up, ~33% screen height, same shell as points sheet
- Content: merchant logo (40×40 circle, red gradient) + name "萌宠屋" (16px bold), coupon value "满50减10" (24px, weight 900, #FF3B30, DIN Alternate font for numbers), expiry "有效期至 2026-03-15" (13px, #999), bonus tag "🪙 +30 积分" (pill, #FFF8E1 background, #E5A600 text)
- Actions: "查看详情" primary button (gradient #FF5E54→#FF3B30, white text, full radius 24px, shadow), "关闭" text button (#999)

Opening Animation:
- Duration: 0.8s total
- Chest lid opens upward + gold particle burst from center
- Rare chest: enhanced particle density
- Task chest: particle colors follow collar color instead of gold
- Map interaction locked during animation to prevent accidental taps

Tab Bar (fixed bottom):
- Height: 56px + platform safe area
- White 95% opacity, backdrop-filter blur 12px, top border 0.5px #F0F0F0
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的
- Active: full opacity icon, text #E5A600 bold (10px)
- Inactive: icon 40% opacity, text #999 (10px)

**States:**
- Default: Apple Maps loaded at street level, chests scattered, quest bar showing daily status, marquee scrolling world messages
- Loading: Map loading, chests not yet visible, quest bar shows skeleton
- Chest entrance: Chests animate in with staggered entrance (scale 0→1 + translateY, 0.4s each, 80ms delay between)
- Quest complete: Quest bar glows with collar-color ring, toast "🎉 今日任务全部完成！" + medium haptic feedback
- Task chest spawned: 🎯 marker appears on map near user with collar-color glow
- Empty — no chests: Centered illustration (120×120) + "附近暂无宝箱，换个地方遛遛看" (15px, #999)
- Empty — city not open: "当前区域暂未开放寻宝，敬请期待"
- Error — weak GPS: Alert bar (warning type) persists: "GPS 信号弱，请移至空旷处"
- Error — network: Alert bar (error type) + "重试" button
- Error — location permission denied: Full-screen overlay, white background, illustration (160×160) + "寻宝需要定位权限" (18px bold) + description (14px, #666) + "去设置" primary button

**Style:**
- Design system: PawQuest custom branded system — warm gamification, soft rounded aesthetics
- Visual tone: Generous border radii, gentle shadows, warm surfaces. Approachable without being cartoonish
- Map style: Apple Maps light theme — clean, quiet cartography that lets game elements pop
- Map zoom: Street level, ~300-500m visible range
- Primary accent: #FFB800 (gold)
- Commerce accent: #FF3B30 (red)
- Personalization accent: User's collar color (use #3498DB Ocean Blue in design example)
- Border radius: 8px (tags, marquee), 12px (status bar, quest bar, dropdown), 16px (cards, sheets), 24px (large buttons)
- Theme: Light only
- Frosted glass: backdrop-filter blur on all floating elements, with graceful degradation to solid semi-transparent backgrounds on lower-end devices
- Shadows: 4-level system — sm (buttons), md (floating cards), lg (dropdowns/sheets), colored (CTAs)
- Glow rings: Collar-color with pulsing opacity, used on activity button, quest bar (complete state), and task chest marker
- Typography: PingFang SC (iOS) / Noto Sans SC (Android) for text, DIN Alternate for display numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- Map SDK: AMap (高德地图), styled to resemble Apple Maps light theme
- All text in Chinese (Simplified)
- Emoji-based iconography for map markers and UI elements
- Medium haptic feedback on entering 50m range (platform-adaptive)
- Map locked during opening animation to prevent accidental interaction
- Quest progress updates passively — user actions (opening chests, walking) auto-count without requiring explicit start
- Task chest spawns within 50m of user's current location when all quests complete
- Activity button only renders when backend returns active campaigns
- Marquee messages delivered via lightweight push/polling, hidden when queue empty
- Back navigation: left swipe gesture (iOS) / system back button (Android)
