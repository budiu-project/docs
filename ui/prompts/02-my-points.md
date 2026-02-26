Design a "My Points" page for a cross-platform mobile application (iOS + Android).

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open, earning points and merchant coupons.
Target users: Dog owners (~8,000 users across 5-10 cities in China).
This page: A secondary page showing the user's points balance, expiry warning, and transaction history. Accessed from the treasure map's floating status bar by tapping the points area. Users check their accumulated points and see a chronological log of how they earned them.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. This page is informational rather than interactive, so the design should be calm and readable while maintaining the gold-accented treasure theme. Visually unified across iOS and Android.
Mood: Warm, Accomplishment, Clear Overview.
Visual Strategy: Large bold balance number as visual anchor. Gold (#FFB800) unifies all points-related elements. Card-based sections with generous padding for easy scanning.

**Elements:**

Navigation Bar:
- Total height: system safe area + 44px nav content
- Background: white (#FFFFFF), bottom border 0.5px #F0F0F0
- Left: back chevron "‹" (20px, #333) in 44×44 tap area
- Center: "我的积分" (17px, weight 700, #333)

Points Summary Card:
- Position: 16px margin from nav bar and sides
- Background: white, border-radius 16px, shadow 0 2px 12px rgba(0,0,0,0.08)
- Padding: 28px 24px
- Decorative element: subtle gold radial gradient glow at top-right corner (rgba(255,184,0,0.1), 120px diameter)
- Content (all centered, stacked vertically):
  - Gold coin emoji 🪙 (36px)
  - Balance: "1,280" (40px, weight 900, #333, DIN Alternate font, tabular-nums, thousands separator)
  - Label: "可用积分" (14px, #999, 2px top margin)
  - Expiry warning bar (conditionally visible when points expire within 30 days):
    - 16px top margin from label
    - Background: #FFF8E1, border-radius 8px, padding 8px 16px
    - Content: ⚠️ icon (14px) + "最早一批将于 23 天后过期" (13px, #FF9500)
    - Flex centered with 6px gap

Section Title:
- Text: "积分明细" (16px, weight 700, #333)
- Position: left-aligned at 16px margin, 24px top spacing from card, 12px bottom spacing

Transaction List Container:
- 16px horizontal margin
- Background: white, border-radius 16px, shadow 0 2px 8px rgba(0,0,0,0.06)
- Contains all transaction items

Transaction List Items (show 8 sample entries):
- Each item height: ~68px, padding 14px 16px, gap 12px between icon and text
- Left icon: 36×36 rounded square (border-radius 10px), emoji centered on tinted background:
  - 📦 Points chest: background #FFF0E1
  - 🎁 Merchant chest: background #FFF8E1
  - 🐾 Dog walk check-in: background #E8F9ED
  - 📅 Streak bonus: background #F0E8FF
- Center info:
  - Primary text: source name (15px, weight 500, #333) — e.g., "积分宝箱", "商家宝箱 · 萌宠屋", "遛狗打卡", "连续遛狗签到"
  - Secondary text: timestamp (13px, #999, 2px top margin) — e.g., "今天 14:32", "昨天 19:45"
- Right: points amount "+15" format (17px, weight 700, DIN Alternate font, #FFB800, tabular-nums)
- Separator between items: 0.5px line, color #F5F5F5

Sample transactions (chronological, newest first):
1. 📦 积分宝箱 — 今天 14:32 — +15
2. 🎁 商家宝箱 · 萌宠屋 — 今天 14:15 — +30
3. 🐾 遛狗打卡 — 今天 08:20 — +10
4. 📦 积分宝箱 — 昨天 19:45 — +8
5. 📅 连续遛狗签到 — 昨天 19:30 — +5
6. 📦 积分宝箱 — 昨天 18:52 — +12
7. 🎁 商家宝箱 · 汪星人医院 — 昨天 18:40 — +50
8. 🐾 遛狗打卡 — 昨天 08:15 — +10

Footer Text:
- "积分商城即将上线，敬请期待" (13px, #CCC, centered)
- Padding: 24px vertical

**States:**
- Default: Balance card + transaction list with data
- Loading: Skeleton screens for balance card and list items
- Empty: No transactions — illustration (100×100, 40% opacity) + "还没有积分记录，去开宝箱吧" (14px, #999), centered below section title
- Error — network: Toast notification "网络异常，请稍后重试"

**Style:**
- Design system: PawQuest custom branded system — warm gamification, soft rounded aesthetics
- Primary accent: #FFB800 (gold for all points-related visuals)
- Border radius: 16px (cards), 10px (list icons), 8px (tags)
- Theme: Light only
- Page background: #F7F6F3 (warm off-white)
- Card background: #FFFFFF
- Shadows: md (cards), sm (list container)
- Typography: PingFang SC (iOS) / Noto Sans SC (Android) for text, DIN Alternate for display numbers and points amounts

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- No tab bar visible (sub-page, navigates back via chevron or platform back gesture/button)
- All text in Chinese (Simplified)
- Pull-to-refresh for balance + list
- Infinite scroll pagination for transaction list (20 items per page)
- Scrollable content area below fixed nav bar
- Back navigation: left swipe gesture (iOS) / system back button (Android)
