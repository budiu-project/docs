Design a treasure hunt map page for a mobile (iOS) application.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") where users explore a full-screen map, discover nearby treasure chests, walk into range (50m), and open them for rewards. This is the core gameplay loop.

**Design Philosophy:**
Warm Gamification — game-inspired treasure hunt mechanics wrapped in a warm, approachable visual language that feels like a daily lifestyle companion rather than a mobile game.
Mood: Warm, Discovery, Casual Delight, Outdoor Vitality.
Visual Strategy: Gold (#FFB800) as signature accent for treasure/points. Frosted-glass floating layers over full-bleed map. Emoji-based map markers for instant recognition. Micro-animations serve comprehension, not decoration.

**Elements:**

Floating Status Bar (over map):
- Position: below iOS safe area (44px), 16px horizontal margin
- Size: full width minus margins, 44px height
- Style: white 80% opacity, backdrop-filter blur 12px, border-radius 12px, shadow 0 2px 12px rgba(0,0,0,0.08)
- Left section: gold coin icon (16×16) + text "今日 +85 分" (14px, weight 500, #333)
- Center: "3/10" chest progress (14px, weight 500, #666, tabular-nums)
- Right section: coupon icon 🎫 (22px) in 44×44 tap area, red notification dot (8×8) at top-right corner

Alert Bar (conditional, slides in from top):
- Position: directly below status bar, 16px horizontal margin
- Size: 36px height, border-radius 8px
- Types: Warning (#FFF3CD text #856404), Error (#F8D7DA text #721c24), Info (#D1ECF1 text #0c5460)
- Animation: slide down 0.2s ease-out, info type auto-dismiss after 3s
- Sample text: "这个宝箱刚被领走了" (info type)

Full-Screen Map:
- Fills entire screen, all UI floats above it
- Simulated map with subtle terrain: muted earth-tone parks (greens), tan streets, grey building blocks
- Map labels: "朝阳公园", "望京街道", "东风北桥" (10px, rgba(0,0,0,0.25), letter-spacing 2px)
- User position marker: 40×40 circle with gradient (#4A90D9 → #357ABD), dog emoji 🐕 inside, pulsing ring (80×80, rgba(74,144,217,0.15), 2s ease-out infinite)

Treasure Chest Markers (scatter 7 across map):
- Points chest (far): 📦 emoji 28px, distance pill below ("230m" — 11px #666, white 80% background, rounded pill)
- Points chest (openable, within 50m): 📦 28px, bounce animation (translateY -4px, 0.6s ease-in-out infinite), brightened with gold glow (drop-shadow 0 2px 8px rgba(255,184,0,0.5) + brightness 1.15), label shows "可开启" (12px, #34C759, bold, white 90% background)
- Merchant chest (far): 🎁 34px (larger than points), distance pill
- Merchant chest (openable): 🎁 34px, bounce + glow, "可开启" label
- Rare chest (openable): 👑 34px, purple glow ring (radial-gradient rgba(175,82,222,0.4), pulsing scale 1→1.15 over 1.5s), bounce, "可开启" label
- Merchant chest (claimed): 🎁 34px, grayscale + 50% opacity, green checkmark circle (16×16, #34C759 background, white ✓) at bottom-right, label "已领取" (#999)
- Points chest (very far): 📦 28px, "520m" label

Bottom Controls (floating above tab bar):
- Position: above tab bar + 16px bottom spacing, 16px horizontal margin
- Left: Filter button — capsule shape, 36px height, 14px horizontal padding, white background, shadow (0 2px 12px rgba(0,0,0,0.08)), ⚙️ icon + "筛选" text (13px, weight 500, #333)
- Right: Locate button — 44×44 circle, white background, shadow, 📍 icon (20px) centered

Filter Dropdown (expanded state):
- Position: above filter button
- White background, border-radius 12px, shadow 0 4px 20px rgba(0,0,0,0.12)
- 3 options stacked: "全部" (active — #E5A600, bold), "📦 积分宝箱", "🎁 商家宝箱"
- Each option: 12px vertical padding, 20px horizontal padding, 14px text, separated by 1px #F5F5F5 border
- Active option highlighted with gold text

Points Reward Bottom Sheet:
- Slides up from bottom, ~25% screen height
- White background, top border-radius 16px, drag handle (36×4px, #F0F0F0, centered)
- Content centered: gold coin 🪙 (48px), "+15 积分" (32px, weight 900, #FFB800), "当前共 1,295 积分" (14px, #999)
- Semi-transparent overlay behind (rgba(0,0,0,0.3))

Merchant Coupon Reward Bottom Sheet:
- Slides up, ~33% screen height, same shell as points sheet
- Content: merchant logo (40×40 circle, red gradient) + name "萌宠屋" (16px bold), coupon value "满50减10" (24px, weight 900, #FF3B30), expiry "有效期至 2026-03-15" (13px, #999), bonus tag "🪙 +30 积分" (pill, #FFF8E1 background, #E5A600 text)
- Actions: "查看详情" primary button (gradient #FF5E54→#FF3B30, white text, full radius 24px, shadow), "关闭" text button (#999)

Tab Bar (fixed bottom):
- Height: 56px + 34px safe area
- White 95% opacity, backdrop-filter blur 12px, top border 0.5px #F0F0F0
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的
- Active: full opacity icon, text #E5A600 bold (10px)
- Inactive: icon 40% opacity, text #999 (10px)

**States:**
- Default: Map loaded with chests scattered, chests animate in with staggered entrance (scale 0→1 + translateY, 0.4s each, 80ms delay between)
- Loading: Map skeleton, chests not yet visible
- Empty — no chests: Centered illustration (120×120) + "附近暂无宝箱，换个地方遛遛看" (15px, #999)
- Empty — city not open: "当前区域暂未开放寻宝，敬请期待"
- Error — weak GPS: Alert bar (warning type) persists: "GPS 信号弱，请移至空旷处"
- Error — network: Alert bar (error type) + "重试" button
- Error — location permission denied: Full-screen overlay, white background, illustration (160×160) + "寻宝需要定位权限" (18px bold) + description (14px, #666) + "去设置" primary button

**Style:**
- Visual style: Warm gamification with iOS-native feel
- Primary accent: #FFB800 (gold)
- Commerce accent: #FF3B30 (red)
- Border radius: 12px (status bar, dropdown), 16px (cards, sheets), 24px (large buttons)
- Theme: Light only
- Page background: Simulated map (earth tones)
- Shadows: Frosted glass on floating elements

**Constraints:**
- iOS native app (375×812 viewport for design)
- Map SDK: AMap (高德地图)
- All text in Chinese (Simplified)
- SF Symbols + emoji for iconography
- Haptic feedback on entering 50m range (UIImpactFeedbackGenerator.medium)
- Map locked during opening animation to prevent accidental interaction
