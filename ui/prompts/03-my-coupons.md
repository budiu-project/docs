Design a "My Coupons" page for a cross-platform mobile application (iOS + Android).

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open, earning points and merchant coupons.
Target users: Dog owners (~8,000 users across 5-10 cities in China).
This page: A secondary page listing all merchant coupons the user has collected from treasure chests. Organized by status tabs (active vs expired). Accessed from the treasure map's floating status bar coupon icon. Users come here to review and use their coupons at partner pet businesses.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. This page uses ticket/coupon visual metaphors (semi-circle cutouts) to make digital coupons feel tangible and valuable. Red (#FF3B30) dominates as the commerce color. Visually unified across iOS and Android.
Mood: Organized, Valuable Collection, Ready to Use.
Visual Strategy: Coupon cards with physical ticket aesthetic (cutout edges). Clear active/expired visual distinction through color saturation. Red CTAs for immediate action.

**Elements:**

Navigation Bar:
- Total height: system safe area + 44px nav content
- Background: white (#FFFFFF)
- Left: back chevron "‹" (20px, #333) in 44×44 tap area
- Center: "我的券包" (17px, weight 700, #333)
- On page entry: automatically clear the red notification dot on the map page's coupon icon

Status Tab Bar:
- Position: directly below nav bar, no gap
- Height: 44px, background white
- 2 tabs side by side, equal width: "未使用(3)" | "已过期(2)"
- Active tab: text #FF3B30, weight 700, bottom indicator bar (3px height, 40px width, centered under text, #FF3B30, border-radius 2px)
- Inactive tab: text #999, weight 500
- Font size: 15px for both states
- Default: "未使用" tab active
- Supports horizontal swipe gesture to switch tabs

Active Coupon Cards (show 3 cards):
- Position: below tab bar, 16px horizontal margin, 12px vertical gap between cards, 12px top margin
- Each card: white background, border-radius 12px, shadow 0 2px 8px rgba(0,0,0,0.06), horizontal layout (left section + right section), total height ~120px

- Left section (width 90px, flex-shrink 0):
  - Background: linear-gradient 135deg #FF5E54 → #FF3B30
  - Border-radius: 12px on left corners only
  - Ticket cutout effect: two 12px diameter semi-circles on the right edge (one at top, one at bottom), filled with page background #F7F6F3
  - Coupon value text: centered vertically and horizontally, 18px, weight 900, white
  - Multi-line format: "满50\n减10", single-line for "8折券" or "免费\n体检"

- Right section (flex 1, padding 12px):
  - Top: merchant logo (28×28 circle, gradient background, single Chinese character in white bold) + merchant name (15px, weight 700, #333), 8px gap
  - Middle: usage condition (13px, #666), 4px below merchant row
  - Bottom row (flex, space-between, align-center, 8px top margin):
    - Left: expiry text (12px, #999) — e.g., "有效期至 03-15"
    - If expiring within 3 days: text turns #FF3B30 — "即将过期 · 03-01"
    - Right: "去使用" button — padding 5px 14px, border-radius 16px, background linear-gradient(135deg, #FF5E54, #FF3B30), white text, 13px, weight 600

- Press feedback: entire card scales to 0.98 on touch

3 sample active coupons:
1. 萌宠屋 — "满50\n减10" — "满50元可用" — "有效期至 03-15" (logo: pink-red gradient #FF9F9F→#FF6B6B, letter "萌")
2. 汪星人宠物医院 — "免费\n体检" — "新客专享" — "有效期至 03-20" (logo: blue gradient #6BC5E8→#4A90D9, letter "汪")
3. 毛孩子美容 — "8折券" — "洗护服务可用" — "即将过期 · 03-01" (logo: orange gradient #FFB347→#FF9500, letter "毛")

Expired Coupon Cards (hidden by default, shown when "已过期" tab active):
- Same card layout as active, with differences:
  - Left section background: linear-gradient(135deg, #DDD, #CCC)
  - All right-section text: color #CCC
  - No "去使用" button
  - Bottom-right shows text label "已过期" (13px, #CCC)
  - Logo backgrounds also greyed out: linear-gradient(135deg, #CCC, #AAA)

2 sample expired coupons:
1. 宠乐汇 — "满30\n减5" — "满30元可用" — "已过期 02-10" (letter "宠")
2. 爪爪乐园 — "9折券" — "全场通用" — "已过期 02-05" (letter "爪")

Empty States:
- Active tab empty: large emoji 🎫 (64px, 40% opacity) + "还没有优惠券，去开商家宝箱吧" (14px, #999), centered in scroll area with 80px top padding
- Expired tab empty: same layout + "没有已过期的优惠券"

**States:**
- Default: "未使用" tab active with 3 coupon cards displayed
- Loading: Skeleton card placeholders (3 cards with shimmer animation)
- Empty — no active coupons: Empty state with illustration
- Empty — no expired coupons: Empty state with illustration
- Error — network: Toast "网络异常，请稍后重试"

**Style:**
- Design system: PawQuest custom branded system — warm gamification, soft rounded aesthetics
- Commerce color: #FF3B30 (red for coupons, CTAs, active tab)
- Border radius: 12px (cards), 16px (small buttons), 24px (large buttons)
- Theme: Light only
- Page background: #F7F6F3 (warm off-white)
- Card background: #FFFFFF
- Shadows: sm (coupon cards)
- Typography: PingFang SC (iOS) / Noto Sans SC (Android) for text

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- No tab bar visible (sub-page)
- All text in Chinese (Simplified)
- Pull-to-refresh for coupon list
- Tapping coupon card or "去使用" button navigates to coupon detail page
- Expired coupon cards are not tappable
- Back navigation: left swipe gesture (iOS) / system back button (Android)
