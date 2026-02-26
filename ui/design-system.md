# PawQuest Design System

自定义品牌设计系统，跨 iOS / Android 双端统一视觉，交互跟随平台惯例。

---

## 设计哲学

**Warm Gamification（暖色游戏化）** — 轻盈圆润的视觉基调，游戏化寻宝机制包裹在温暖亲和的生活感界面中。克制程度接近小红书，不是多邻国。

**核心原则：**

1. **温暖不幼稚** — 圆角、暖色、emoji 图标传递亲和力，但不使用卡通插画或夸张动效
2. **地图优先** — 寻宝页是核心，全屏地图上所有 UI 浮层轻量化，不遮挡探索视野
3. **项圈色即身份** — 用户的项圈硬件颜色作为个性化主线，贯穿交互反馈（光环、进度条、按钮、粒子），建立物理产品与数字体验的连接
4. **平台尊重** — 视觉 100% 统一，但导航手势、系统返回、状态栏行为跟随各平台原生惯例

**技术基底：**

- 框架：Flutter（自绘引擎，天然视觉一致）
- 主题：`ThemeExtension` 实现项圈色动态取色
- 性能策略：毛玻璃效果在高端机启用，低端机降级为半透明纯色

---

## 色彩体系

分三层：固定品牌色 → 功能语义色 → 动态项圈色。

### 固定品牌色

| 角色 | Token | 色值 | 用途 |
|------|-------|------|------|
| 宝藏金 | color.brand.gold | #FFB800 | 积分、宝箱、主品牌色调 |
| 宝藏金浅 | color.brand.goldLight | #FFF8E1 | 积分标签背景、金色徽章底 |
| 宝藏金深 | color.brand.goldDark | #E5A600 | 选中态 Tab 文字、金色强调 |
| 商家红 | color.brand.merchant | #FF3B30 | 优惠券、商业 CTA、红点 |
| 稀有紫 | color.brand.rare | #AF52DE | 稀有宝箱光环（仅此一处） |

### 功能语义色

| 角色 | Token | 色值 | 用途 |
|------|-------|------|------|
| 成功绿 | color.semantic.success | #34C759 | 可开启状态、已完成勾选 |
| 链接蓝 | color.semantic.link | #007AFF | 可点击文字链接 |
| 警告橙 | color.semantic.warning | #FF9500 | 过期提醒 |
| 错误红 | color.semantic.error | #FF3B30 | 网络异常提示 |
| 提示条-警告 | color.alert.warning | #FFF3CD | GPS 弱信号底色 |
| 提示条-错误 | color.alert.error | #F8D7DA | 网络异常底色 |
| 提示条-信息 | color.alert.info | #D1ECF1 | 宝箱被抢通知底色 |

### 中性色

| 角色 | Token | 色值 | 用途 |
|------|-------|------|------|
| 页面底色 | color.surface.page | #F7F6F3 | 非地图页背景（暖白） |
| 卡片白 | color.surface.card | #FFFFFF | 卡片、浮层背景 |
| 文字主色 | color.text.primary | #333333 | 标题、关键信息 |
| 文字次色 | color.text.secondary | #666666 | 描述文字 |
| 文字弱色 | color.text.tertiary | #999999 | 时间戳、辅助标签 |
| 文字禁用 | color.text.disabled | #CCCCCC | 禁用态、占位符 |
| 分割线 | color.divider.default | #F0F0F0 | 导航栏边框 |
| 分割线浅 | color.divider.light | #F5F5F5 | 列表分隔 |

### 动态项圈色

跟随用户绑定的硬件项圈，每种提供主色、光环色、粒子色双色：

| 项圈 | 主色 | 光环色 | 粒子色 |
|------|------|--------|--------|
| 经典红 | #E74C3C | rgba(231,76,60,0.4) | #FF6B6B / #FF3B30 |
| 海洋蓝 | #3498DB | rgba(52,152,219,0.4) | #6BC5E8 / #4A90D9 |
| 森林绿 | #27AE60 | rgba(39,174,96,0.4) | #6FCF97 / #34C759 |
| 尊享金 | #F1C40F | rgba(241,196,15,0.4) | #FFD700 / #FFB800 |
| 暗夜黑 | #2C3E50 | rgba(44,62,80,0.3) | #BDC3C7 / #ECF0F1 |

Token 命名：`color.collar.primary`、`color.collar.glow`、`color.collar.particleA`、`color.collar.particleB`（动态值）。

未绑定项圈默认使用宝藏金 #FFB800。

---

## 圆角体系

| 级别 | Token | 值 | 用途 |
|------|-------|-----|------|
| xs | radius.xs | 4px | 标签、小徽章 |
| sm | radius.sm | 8px | 跑马灯、提示条、筛选下拉项 |
| md | radius.md | 12px | 状态栏、任务条、筛选按钮、通用卡片 |
| lg | radius.lg | 16px | Bottom Sheet 顶部、任务卡片、奖励卡片 |
| xl | radius.xl | 24px | 大按钮（出发、查看详情、去设置） |
| full | radius.full | 50% | 圆形按钮（定位、活动）、头像、复选框 |

---

## 阴影体系

| 级别 | Token | 值 | 用途 |
|------|-------|-----|------|
| sm | shadow.sm | 0 2px 8px rgba(0,0,0,0.06) | 普通按钮、列表容器 |
| md | shadow.md | 0 2px 12px rgba(0,0,0,0.08) | 浮层卡片、状态栏、任务条 |
| lg | shadow.lg | 0 4px 20px rgba(0,0,0,0.12) | 下拉菜单、Bottom Sheet |
| colored | shadow.colored | 0 4px 12px {color}30 | CTA 按钮带品牌色阴影（商家红/项圈色 30% 透明度） |

---

## 毛玻璃体系

| 级别 | Token | 背景 | 模糊 | 降级方案（低端机） |
|------|-------|------|------|-----------------|
| light | glass.light | white 80% | blur 12px | white 92% 纯色 |
| medium | glass.medium | white 90% | blur 12px | white 95% 纯色 |
| dark | glass.dark | black 50% | blur 8px | black 60% 纯色 |

降级判断：通过设备性能检测（刷新率/内存），低于阈值自动切换。

---

## 间距网格

8px 基准，允许值：4、8、12、16、24、32。

| 场景 | Token | 值 |
|------|-------|-----|
| 页面水平边距 | spacing.page | 16px |
| 卡片内边距（水平） | spacing.card.h | 16px |
| 卡片内边距（垂直） | spacing.card.v | 12-16px |
| 元素间紧凑间距 | spacing.sm | 8px |
| 元素间标准间距 | spacing.md | 12px |
| 区块间距 | spacing.lg | 16-24px |
| 浮层按钮间距 | spacing.md | 12px |

---

## 字体与排版

### 字体栈

| 平台 | 正文 | 数字（等宽） |
|------|------|-------------|
| iOS | PingFang SC | DIN Alternate / SF Mono |
| Android | Noto Sans SC | DIN Alternate / Roboto Mono |

DIN Alternate 用于积分数字、券面金额等需要突出的数值展示。未内嵌时降级到平台等宽字体。

### 字号层级

| 级别 | Token | 字号 | 字重 | 用途 |
|------|-------|------|------|------|
| display | text.display | 32px | 900 (Black) | 奖励数值（"+15 积分"、"满50减10"） |
| title-lg | text.titleLg | 18px | 700 (Bold) | 全屏提示标题（"寻宝需要定位权限"） |
| title | text.title | 16px | 700 | 卡片标题（"今日寻宝任务"）、商家名称 |
| body | text.body | 15px | 400 | 任务名称、列表正文 |
| body-sm | text.bodySm | 14px | 500 | 状态栏文字、进度文字、按钮文字 |
| caption | text.caption | 13px | 400 | 跑马灯、辅助说明、时间戳、方向提示 |
| caption-sm | text.captionSm | 12px | 500/700 | 宝箱标签（"可开启"、"已领取"、"任务奖励"） |
| tab | text.tab | 10px | 400/700 | Tab 栏文字 |
| pill | text.pill | 11px | 400 | 距离标签（"230m"） |

### 排版规则

- 所有数值使用 `tabular-nums`（等宽数字），避免数字变化时文字跳动
- 积分、金额等关键数字用 DIN Alternate 字体 + display 级别
- 中文正文行高 1.5，标题行高 1.3
- 单行截断用省略号，不折行（宝箱标签、跑马灯消息、商家名称）

---

## 通用组件

### 浮层卡片（Floating Card）

地图页上所有悬浮 UI（状态栏、跑马灯、任务条）的容器。

- 结构：圆角容器 + 毛玻璃背景 + 阴影 md
- 统一左右 margin 16px

### Bottom Sheet

任务卡片、积分奖励、商家券奖励的承载容器。

- 顶部圆角 lg (16px)，拖拽条居中（36×4px, #F0F0F0）
- 半透明遮罩 rgba(0,0,0,0.3)
- 关闭方式：点击遮罩 / 下滑拖拽

### 圆形浮层按钮（Floating Action Circle）

定位按钮、活动按钮。

- 44×44，白色背景，阴影 md，圆形
- 内部 emoji 图标 20px 居中
- 按下态：scale 0.95 + 项圈色涟漪（定位按钮）

### 胶囊按钮（Capsule Button）

筛选按钮。

- 高 36px，水平内边距 14px，白色背景，阴影 sm
- 圆角 full（胶囊形）

### CTA 按钮（Primary Action）

"出发"、"查看详情"、"去设置"等主操作按钮。

- 高 44px，圆角 xl (24px)，全宽
- 背景：渐变色（项圈色浅→深 或 商家红渐变）
- 文字：15px weight 700 白色
- 阴影 colored（对应色 30% 透明度）

### 通知红点（Notification Dot）

- 8×8 圆形，#FF3B30，无描边
- 定位于父元素右上角

---

## 平台差异对照

视觉 100% 统一，以下行为跟随各平台惯例：

| 行为 | iOS | Android |
|------|-----|---------|
| 返回导航 | 左滑手势 + 导航栏左箭头 | 系统返回键 + 导航栏左箭头 |
| 状态栏 | 安全区 44px | 系统状态栏高度自适应 |
| 底部安全区 | 34px (Home Indicator) | 导航栏高度自适应 |
| 触觉反馈 | UIImpactFeedbackGenerator.medium | HapticFeedback.mediumImpact |
| 滚动回弹 | iOS 弹性回弹 | Android overscroll glow |

---

## 动效规范

### 寻宝页动效

寻宝页是核心游戏体验，动效服务于"发现"和"奖励"的状态反馈。精致微动效 + 选择性增强，不追求全屏特效。

| 动效 | 描述 | 时长 | 触发 |
|------|------|------|------|
| 宝箱入场 | 依次蹦出（scale 0→1 + translateY），80ms 间隔 | 0.4s/个 | 地图加载完成 |
| 宝箱可开启 | 进入 50m 一次性切换：弹跳 + 金色光晕 + "可开启"标签 | 持续循环 | 用户进入 50m |
| 开箱 | 开盖动画 + 粒子爆散，稀有加强粒子，任务宝箱用项圈色粒子 | 0.8s | 点击可开启宝箱 |
| 脉冲光环 | 外圈呼吸动画（opacity 50%→100%） | 1.5s 循环 | 稀有宝箱/任务宝箱/活动按钮/任务完成态 |
| 任务完成 | 任务条光环脉冲 + toast + 触觉反馈 | 一次性 | 全部每日任务完成 |
| 进度条填充 | 任务条底部进度平滑过渡 | 0.3s | 任务进度变化 |
| 定位按钮 | 项圈色涟漪扩散 | 0.4s | 按下定位按钮 |
| 活动按钮入场 | 右侧滑入 + 弹跳 | 0.5s | 新活动上线 |

### 非寻宝页

保持克制：标准页面转场、列表 fade-in、按钮 press scale (0.97-0.98)，不加额外动效。

### 通用交互反馈

- 按下态：scale 0.97-0.98，0.1s ease
- 触觉反馈：进入 50m 范围、开箱、任务完成时触发 medium impact
- 转场动画：跟随平台默认（iOS slide from right，Android fade/slide）

---

## Design Token 命名约定

所有色彩、间距、圆角、阴影通过统一 Token 引用，不在组件中硬编码值。

Token 分组：
- `color.brand.*` — 固定品牌色
- `color.semantic.*` — 功能语义色
- `color.alert.*` — 提示条底色
- `color.text.*` — 文字色阶
- `color.surface.*` — 背景色
- `color.divider.*` — 分割线
- `color.collar.*` — 动态项圈色（primary / glow / particleA / particleB）
- `radius.*` — 圆角
- `shadow.*` — 阴影
- `glass.*` — 毛玻璃配置
- `spacing.*` — 间距
- `text.*` — 字号层级

主题层级结构：
- 基础主题层：固定品牌色 + 语义色 + 中性色 + 字号 + 间距 + 圆角 + 阴影
- 项圈色扩展层：动态项圈色（5 套预设 + 默认金色降级），切换时所有引用项圈色的组件自动更新
- 毛玻璃扩展层：根据设备性能检测结果决定启用毛玻璃或降级为纯色半透明
