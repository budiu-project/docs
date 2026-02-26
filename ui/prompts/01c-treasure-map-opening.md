Design a treasure hunt map page for a cross-platform mobile application (iOS + Android). This shows the **chest opening reward** state — the user has just opened a treasure chest and is viewing the reward bottom sheet.

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open while walking their dogs, earning points and merchant coupons along the way.
Target users: Dog owners (~8,000 users across 5-10 cities in China) who walk their dogs regularly.
This page: The primary tab page ("寻宝") at the moment of reward reveal. The user walked within 50m of a chest, tapped to open it, the opening animation has played, and a reward bottom sheet has slid up showing the prize. Show TWO reward variants side by side or pick one to feature prominently.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. Visually unified across iOS and Android.
Visual Strategy: This is the "payoff moment" — the reward reveal should feel celebratory but restrained, using gold accents and gentle scale animations rather than overwhelming particle effects.

**Collar Color Personalization:**
In the design, use "Ocean Blue" (#3498DB) as the example collar color.

**Elements:**

Background: Full-screen Apple Maps with treasure chest markers. Quest bar visible above tab bar showing "1/3 进行中" (quest is active). Status bar and marquee at top.

Opening Animation (post-state, show the result):
- The opened chest marker on map shows a brief gold sparkle residue (2-3 small gold particles fading out)
- The chest that was opened is no longer on the map (removed after opening)

**Reward Variant A — Points Reward Bottom Sheet:**
- Slides up from bottom, ~25% screen height
- White background, top border-radius 16px, drag handle (36×4px, #F0F0F0)
- Semi-transparent overlay: rgba(0,0,0,0.3)
- Content centered vertically within sheet:
  - Gold coin emoji 🪙 (48px), with subtle pop-in animation (scale 0→1.1→1, 0.3s)
  - "+15 积分" (32px, weight 900, #FFB800, DIN Alternate font, tabular-nums)
  - "当前共 1,295 积分" (14px, #999, regular weight)
- Dismiss: tap overlay, swipe down, or auto-dismiss after 3s

**Reward Variant B — Merchant Coupon Reward Bottom Sheet:**
- Slides up from bottom, ~33% screen height
- White background, top border-radius 16px, drag handle
- Semi-transparent overlay: rgba(0,0,0,0.3)
- Content:
  - Merchant logo: 40×40 circle with red gradient background (#FF5E54 → #FF3B30), white store icon inside
  - Merchant name: "萌宠屋" (16px, weight 700, #333), right of logo
  - Coupon value: "满50减10" (24px, weight 900, #FF3B30, DIN Alternate for numbers), centered below
  - Expiry: "有效期至 2026-03-15" (13px, #999)
  - Bonus tag: pill shape, "🪙 +30 积分" (12px, #E5A600 text, #FFF8E1 background, border-radius 12px, padding 4px 10px)
  - 20px gap
  - "查看详情" primary button: full width minus 40px padding, 44px height, border-radius 24px, gradient #FF5E54→#FF3B30, white text 15px weight 700, shadow 0 4px 12px rgba(255,59,48,0.3)
  - "关闭" text button: centered below, 13px, #999, 44px tap height

Quest Bar (visible behind overlay):
- Showing "1/3 进行中" state with collar-color progress line

Tab Bar (fixed bottom, visible behind overlay):
- 4 tabs: 🏠首页, 📦寻宝 (active), 🗺️轨迹, 👤我的

**States:**
- Points reward (shown): Gold coin + points amount in bottom sheet
- Merchant coupon reward (shown): Merchant info + coupon value + action buttons in bottom sheet

**Style:**
- Design system: PawQuest custom branded system
- Gold accent #FFB800 for points rewards, Red accent #FF3B30 for merchant/coupon elements
- Personalization accent: collar color (#3498DB Ocean Blue) on quest bar
- Border radius: 16px (bottom sheets), 24px (action buttons), 12px (bonus tag pill)
- Shadows: lg (bottom sheets), colored (CTA buttons)
- Typography: PingFang SC (iOS) / Noto Sans SC (Android), DIN Alternate for reward numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- All text in Chinese (Simplified)
- DIN Alternate font for all numeric displays (points, coupon values)
- Bottom sheet overlay does not cover tab bar (tab bar remains interactive)
