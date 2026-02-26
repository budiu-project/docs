Design a "Coupon Detail" page for a cross-platform mobile application (iOS + Android).

**Context:**
PawQuest Treasure Hunt — a gamified treasure hunt feature that motivates dog walking by placing treasure chests on a map for users to discover and open, earning points and merchant coupons.
Target users: Dog owners (~8,000 users across 5-10 cities in China).
This page: A tertiary detail page showing the full coupon information — ticket-style face, usage rules, merchant location, and a prominent CTA to present the coupon in-store. Accessed from the coupon list or directly from the chest-opening reward sheet. This is the conversion point where digital coupon becomes in-store usage.

**Design Philosophy:**
PawQuest custom branded design system — warm gamification with soft, rounded aesthetics. This page is the climax of the coupon visual metaphor: the ticket card with semi-circle cutouts and dashed tear line makes the digital coupon feel like a real physical ticket. Clear information hierarchy guides the user from "what is this coupon" to "how do I use it" to "take me there." Visually unified across iOS and Android.
Mood: Valuable, Clear, Action-Ready.
Visual Strategy: Ticket aesthetic at its fullest expression. Information flows top-down: coupon face → rules → merchant → action. Red (#FF3B30) CTA anchored at bottom for constant visibility.

**Elements:**

Navigation Bar:
- Total height: system safe area + 44px nav content
- Background: white (#FFFFFF), bottom border 0.5px #F0F0F0
- Left: back chevron "‹" (20px, #333) in 44×44 tap area
- Center: "券详情" (17px, weight 700, #333)

Coupon Ticket Card:
- Position: 16px margin from nav and sides
- Background: white, border-radius 16px, shadow 0 2px 12px rgba(0,0,0,0.08)
- Padding: 28px 24px
- Ticket cutout effect: two 16px diameter semi-circles, one on left edge and one on right edge, both positioned at 60% from top of card, filled with page background color #F7F6F3
- Dashed tear line: horizontal dashed border (2px dashed #F0F0F0) spanning the card width at 60% height, 16px inset from left and right edges
- Content (all centered vertically above the tear line):
  - Merchant row: logo (48×48 circle, gradient background #FF9F9F→#FF6B6B, letter "萌" in 20px white weight 900) + name "萌宠屋" (18px, weight 700, #333), 10px gap between logo and name, flex centered
  - Coupon value: "满50减10" (36px, weight 900, #FF3B30, DIN Alternate font for numbers), 16px below merchant row
  - Expiry: "有效期至 2026-03-15" (14px, #999), 8px below value
  - Urgent expiry variant: if within 3 days, text becomes #FF3B30 with prefix "即将过期 · "

Usage Rules Section:
- Position: 24px below ticket card, 16px horizontal margin
- Title: "使用规则" (16px, weight 700, #333), 12px bottom margin
- Rules container: white background, border-radius 12px, padding 16px, shadow 0 2px 8px rgba(0,0,0,0.06)
- Each rule line:
  - Bullet prefix "·" (absolute positioned, left 0, #999, weight 700)
  - Text: 14px, #666, line-height 1.8, padding-left 12px
- Sample rules:
  1. 满50元可用，不可叠加使用
  2. 仅限到店消费使用
  3. 每单限用一张
  4. 不可兑换现金

Merchant Info Section:
- Position: 24px below rules section, 16px horizontal margin
- Title: "商家信息" (16px, weight 700, #333), 12px bottom margin
- Info container: white background, border-radius 12px, padding 16px, shadow 0 2px 8px rgba(0,0,0,0.06)
- Address row:
  - 📍 icon (18px, #999, flex-shrink 0)
  - Text: "朝阳区望京街道 SOHO T3 一层 108 号" (14px, #333), 8px left gap
  - Max 2 lines
- Phone row (12px below address):
  - 📞 icon (18px, #999, flex-shrink 0)
  - Phone number: "010-5678-1234" (14px, #007AFF, tappable — triggers system dialer), 8px left gap
  - Navigation button (right-aligned, margin-left auto, flex-shrink 0):
    - Border: 1.5px solid #FF3B30, no fill
    - Border-radius 16px, padding 5px 14px
    - Content: 🧭 icon + "导航" text (13px, weight 600, #FF3B30), 4px gap
    - On tap: opens system map picker (AMap / Baidu / Apple Maps on iOS, AMap / Baidu / Google Maps on Android) with merchant coordinates

Fixed Bottom Action Bar:
- Position: fixed at page bottom
- Height: 68px total (10px top padding + 48px button + 10px + platform safe area)
- Background: white, top border 0.5px #F0F0F0
- Button: "到店出示此券"
  - Full width (16px horizontal margin), 48px height
  - Background: linear-gradient(135deg, #FF5E54, #FF3B30)
  - Text: white, 17px, weight 700
  - Border-radius: 24px
  - Shadow: 0 4px 16px rgba(255,59,48,0.3)
  - Press feedback: scale 0.97 on touch (0.15s transition)

QR Code Presentation Modal (triggered by bottom button):
- Full-screen white overlay, z-index above everything
- Screen brightness automatically set to maximum (restores on close)
- Close button: top-right corner (44px below safe area, right 8px), ✕ character (24px, #999) in 44×44 tap area
- Content (centered vertically):
  - Merchant name: "萌宠屋" (16px, #666)
  - Coupon value: "满50减10" (24px, weight 900, #FF3B30, DIN Alternate font for numbers), 8px below name
  - QR code placeholder: 200×200 square, 3px solid #333 border, border-radius 12px, grid pattern overlay to simulate QR texture, centered text "券码区域" (14px, #999), 32px below value
  - Hint text: "请出示给商家扫码核销" (14px, #999), 24px below QR

**States:**
- Default: Full coupon detail with active "到店出示此券" button
- Loading: Ticket card skeleton + rules skeleton
- Expired coupon: ticket card overlaid with grey mask (40% opacity), "已过期" watermark text (20px, #999, rotated -15°) centered on card. Bottom button disabled: background #CCC, text "优惠券已过期", not tappable
- QR Modal open: full-screen white with QR code, brightness maximized
- Error — network: Toast "网络异常，请稍后重试"

**Style:**
- Design system: PawQuest custom branded system — warm gamification, soft rounded aesthetics
- Commerce color: #FF3B30 (red for coupon value, CTA, navigation button)
- Link color: #007AFF (phone number)
- Border radius: 16px (ticket card), 12px (rule/info containers), 24px (CTA button), 16px (nav button)
- Theme: Light only
- Page background: #F7F6F3 (warm off-white)
- Card background: #FFFFFF
- Shadows: md (ticket card), sm (rule/info containers), colored (CTA button)
- Typography: PingFang SC (iOS) / Noto Sans SC (Android) for text, DIN Alternate for display numbers

**Constraints:**
- Cross-platform: Flutter, 375×812 reference viewport
- No tab bar visible (sub-page)
- All text in Chinese (Simplified)
- Content scrolls vertically, bottom 80px padding to clear fixed footer
- Back navigation: chevron tap, left swipe gesture (iOS) / system back button (Android)
- Phone number tap triggers system dial confirmation
- Navigation button triggers system map app picker with merchant coordinates
- QR modal brightness control requires platform screen brightness API
