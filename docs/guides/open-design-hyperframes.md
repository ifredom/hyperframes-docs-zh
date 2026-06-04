---
name: HyperFrames切换
description: |
  Produce a HyperFrames-valid HTML composition — paused GSAP timeline, data
  attributes, scene structure — that any AI coding agent can immediately
  refine with `npx hyperframes lint` and `npx hyperframes preview`. Use when
  the brief mentions "video", "reel", "motion graphic", "title card",
  "animated explainer", or pairs Open Design with HyperFrames for export.
triggers:
  - "hyperframes"
  - "video"
  - "reel"
  - "motion graphic"
  - "animated explainer"
  - "title card"
  - "kinetic typography"
  - "动效视频"
  - "视频海报"
od:
  mode: prototype
  platform: desktop
  scenario: marketing
  preview:
    type: html
    entry: index.html
  design_system:
    requires: true
    sections: [color, typography, layout, motion]
  example_prompt: "Design a 15-second Instagram reel announcing dark mode for Taskflow (#6C5CE7). Output as a HyperFrames composition I can render locally."
---

# HyperFrames Handoff — 用于开放式设计

> **将此文件拖放到本地的 `skills/hyperframes-handoff/SKILL.md` 处
> [打开设计](https://github.com/nexu-io/open-design)签出，重新启动
> 守护进程，并且技能出现在选择器中。或者将其附加到新的聊天中
> 作为一次性的。**

这项技能教会开放设计发出**有效的初稿**
[HyperFrames](https://github.com/heygen-com/hyperframes) 组合 — 普通
HTML + CSS + 暂停的 GSAP 时间线。 CLI（`npx HyperFrames渲染
index.html`) 将 HTML 转换为 MP4。您编写 HTML；用户运行
本地渲染。

**HyperFrames 取代了默认的视频工件工作流程。** 不要发出
React/Babel 组合，不要调用其他原型技能，不要使用
沙盒 iframe 的挂钟播放用于计时决策。纯 HTML +
仅 GSAP。处理 [`claude-design-hyperframes.md`](https://github.com/heygen-com/hyperframes/blob/main/docs/guides/claude-design-hyperframes.md)
配套文档作为 **HyperFrames 结构规则的上游规范** —
下面的规则将其压缩为开放设计在发布时所需的内容，但是
该文件是着色器目录、骨架变体和
边缘情况。

---

## 你的角色

**您生成了有效的初稿，而不是最终渲染。** 打开设计
优点是视觉识别（由活跃的 `DESIGN.md` 驱动）、布局和
品牌准确的内容决策。用户（或其编码代理）处理
动画打磨、时间微调以及交接后的制作质量检查。

用户的工作流程：

1. **开放设计**（您）——从活动中选择调色板+版式
   `DESIGN.md`，填充场景内容，放置第一遍GSAP入口和
   场景中的活动，选择 2-3 个关键时刻的着色器过渡
2. **保存到磁盘** — Open Design 将项目写入
   `.od/projects/<id>/`（真正的`cwd`，代理就绪）
3. **任何 AI 编码智能体**（Claude Code、Codex、Cursor，...） — `npx hyperframes
   lint`, `npxHyperFrames预览`，然后迭代计时、缓动、着色器
   选择、节奏

您的输出必须是编码代理可以打开和的**有效起点
立即完善**——无需进行结构性修复。

### 您优化的目的

- 活动的 `DESIGN.md` 调色板 + 版式绑定到 `:root` （从不
  当调色板处于活动状态时自由设置调色板）
- 每个场景的强大视觉布局（层次结构、间距、视频的可读性
  大小 — 60px+ 标题，20px+ 正文）
- 讲述故事的场景内容（标题、统计数据、文案、图像）
- 结构有效性（以零错误通过 `npx hyperframes lint`）
- 根据心情选择适当的着色器（使用目录
  [hyperframes.heygen.com/catalog](https://hyperframes.heygen.com/catalog))
- 视频类型的合理场景数和持续时间

### 打码剂在你之后打磨什么

您可以使用入口补间、呼吸运动和着色器来交付每个场景
过渡。视频以初稿的全动态播放。这
代理进行**编辑区细化**：缓和曲线调整、错开时间、
场景持续时间微调、更丰富的场景中活动、着色器交换、
生产质量保证。

---

## 硬规则（在发出 `<artifact>` 之前必须通过）

这些是超框架——结构性的且不可协商的。开放式设计
五维自检门必须全部验证完毕后才能发射。

1. **单个 HTML 文件。** `<!doctype html>` 到 `</html>`，所有 CSS 内联，
   从 CDN 加载的 GSAP。没有构建步骤。
2. **根组合元素。** 单个 `<div id="stage">` 具有：
   - `data-composition-id="<kebab-name>"`
   - `data-start="0"`
   - `data-width` / `data-height` （例如 `1080` × `1920` 为 9:16，`1920` ×
     `1080` 代表 16:9，`1080` × `1080` 代表正方形）
   - `data-duration="<total-seconds>"` 匹配场景持续时间的总和
3. **场景是 `#stage` 的子级。** 每个场景都是 `<div class="scene
   剪辑">` 与：
   - `data-start="<seconds-from-zero>"`
   - `data-duration="<scene-seconds>"`
   - `data-track-index="0"`（HyperFrames 使用轨道进行分层；视觉
     场景共享轨道 0，除非您故意重叠）
   - 内部有一个 `.scene-content` 包装器，用于保存可读内容
     （标题、统计数据、图像）。实时装饰（发光、颗粒、小插图）
     直接位于 `.scene` 内部，但 **外部** `.scene-content`。
4. **GSAP 时间线注册已暂停。** 使用以下命令创建的单个时间线
   `gsap.timeline({ paused: true })` 并注册于
   `window.__timelines = window.__timelines || {}; window.__timelines["<comp-id>"] = tl;`。
   这就是使构图具有确定性的可搜索性的原因——
   HyperFrames 引擎驱动播放头。
5. **`tl.from()` 用于入口。** 从屏幕外/不可见到
   resting CSS position.将每个场景的第一个补间偏移 0.1–0.3 秒
   避免跳切。
6. **每个场景中的场景中活动。** 每个可见元素都在移动
   其进入后。静止背景上的静止元素是 JPEG
   进度条。每个场景至少使用下表中的 2 个模式。
7. **着色器过渡仅在场景边界**，并且最多 2-3 个
   整个视频。使用 HyperFrames 的内置着色器块
   （`flash-through-white`、`whip-pan`、`cinematic-zoom`、`glitch`、
   `ripple-waves`、`light-leak`、`cross-warp-morph`、`chromatic-radial-split`、
   `swirl-vortex`、`gravitational-lens`、`domain-warp-dissolve`、`ridged-burn`、
   `sdf-iris`、`thermal-distortion`)。其他地方都很难。
8. **没有用户未提供的外部资源。**使用纯色、CSS
   渐变、内联 SVG、`data:` 图像。参考用户上传的
   按保存的文件名显示图像；不要发明股票网址。
9. **`preview.html` 令牌转发** — 发出同级 `preview.html`
   在 iframe 中加载 `index.html` 并转发 URL 哈希令牌 (`?frame=…`
   用于擦洗）。骨架位于§6。

---

## 第 1 步——理解简介

**门：** 您可以命名主题、时长、长宽比，以及至少一个
视觉方向的来源。

开放设计的 `RULE 1` 已经涵盖了这一点 - 第 1 回合是 `<question-form>`
当简报稀疏时。 **不要跳过视频简介**；踱步
决策取决于早期的锁定持续时间和纵横比。

按可靠性顺序输入：

1. **主动 `DESIGN.md`** （最强） — 开放设计在以下情况下始终有一个界限：
   这个技能运行。阅读其调色板、版式和动作部分；绑定
   逐字记录到 `:root` 上。
2. **附件** — 屏幕截图、PDF、品牌指南；我的任何信号
   Active DS 尚未涵盖。
3. **粘贴的内容** — 十六进制代码、副本、脚本、确切的持续时间。
4. **网络研究**（`WebFetch` + grep for hex） - 仅当用户命名
   品牌和活动 DS 不是他们的。

---

## 第 2 步 — 选择骨架，填写身份

**门：** 工作 `index.html` 与活动 DS 的调色板一起存在，并且
`:root` 上的排版。即使场景为空，预览也会呈现。

| 类型                      | 方面 | 期间  | 场景 |
| ------------------------- | ------ | --------- | ------ |
| 社交卷轴               | 9:16   | 10–15秒    | 5–7    |
| 发布预告片             | 16:9   | 15–25秒    | 7–10   |
| 产品讲解员         | 16:9   | 30-60秒    | 10–18  |
| 电影片名           | 16:9   | 45-90年代    | 7–12   |

从活动的 `DESIGN.md` 绑定 `:root`：

```css
:root {
  /* From active DESIGN.md — never invented */
  --bg: var(--ds-canvas);
  --ink: var(--ds-foreground);
  --accent: var(--ds-accent);
  --muted: var(--ds-muted);
  --font-display: var(--ds-display);
  --font-body: var(--ds-body);
}
```

如果活动 DS 使用不同的令牌名称，请为它们起别名 - 但**总是
从 DS 文件中获取值**，切勿从内存中硬编码十六进制。

---

## 第 3 步 — 填充场景（内容 + 动画）

**门：** 每个场景都有可见的内容，至少有 2 个动画模式
桌子和中间的活动。没有场景是静态幻灯片。

### 3a.内容位于 `.scene-content` 内

```html
<div class="scene clip" data-start="10.0" data-duration="3.0" data-track-index="0">
  <div class="scene-content">
    <h1 id="s3-title" class="display">$1.9 Trillion</h1>
    <p id="s3-sub" class="body-text">processed annually</p>
    <div id="s3-bar-chart"><!-- ... --></div>
  </div>
  <div class="glow" aria-hidden="true"></div>
</div>
```

### 3b.入口补间（每个场景偏移 0.1–0.3 秒）

```js
// === SCENE 3 (data-start=10.0) ===
tl.from("#s3-title", { y: 40, autoAlpha: 0, duration: 0.6, ease: "power3.out" }, 10.3);
tl.from("#s3-sub",   { y: 20, autoAlpha: 0, duration: 0.5, ease: "power2.out" }, 10.7);
tl.from("#s3-bar-chart", { scaleY: 0, transformOrigin: "bottom", duration: 0.8, ease: "expo.out" }, 11.0);
```

### 3c.场景中的活动（这是视频与幻灯片的区别）

| 元素            | 场景中的动作                         | 图案                                                                 |
| ------------------ | ---------------------------------------- | ----------------------------------------------------------------------- |
| 统计/数字      | 计数器从 0 → 目标                  | `tl.to({n:0}, { n: target, duration, onUpdate: …, ease: "power2.out" })` |
| SVG 线/路径    | 实时绘制自己                | 来自 `pathLength → 0` 的 `strokeDashoffset`                                 |
| 标题/字标   | 字符一一输入              | `tl.from(chars, { autoAlpha: 0, y: 8, stagger: 0.04 })`                  |
| 标志/锁定      | 微妙的垂直漂移                    | `tl.to(el, { y: -6, duration: sceneLength, ease: "sine.inOut" })`        |
| 图表/条形图       | 条形按顺序填充                   | `tl.from(bars, { scaleY: 0, transformOrigin: "bottom", stagger: 0.08 })` |
| 图片/截图 | 慢速缩放：`scale: 1 → 1.03`             | 肯·伯恩斯 — `tl.to(img, { scale: 1.03, duration: sceneLength, ease: "none" })` |
| 背景发光    | 不透明度脉冲                            | `tl.to(".glow", { opacity: 0.6, duration: 1.5, ease: "sine.inOut", yoyo: true, repeat: 1 })` |

**每个场景最少：** 入口补间 + 至少一个连续运动
（浮动、计数器、缩放或发光）。

### 3d.通过阅读时间调整场景持续时间

| 显示文字                | 最短持续时间 |
| --------------------------- | ------------ |
| 无文字（英雄、图标）        | 1.5–2秒       |
| 1–3 个字                   | 2-3秒         |
| 4–10 个字                  | 3-4秒         |
| 11–20 个字                 | 4-6秒         |
| 21–35 个字                 | 6-8秒         |
| 35+字                   | 分割场景 |

**硬上限：每个场景 5 秒**除非您说出具体原因（英雄保持、
电影推动，长计数器动画）。

当您更改场景的持续时间时，请在每个后续场景中更新 `data-start`
场景以保持它们端到端平铺，并将 `#stage` 的 `data-duration` 更新为
匹配总数。

### 3e.变化缓和

在整个时间线上至少使用 3 种不同的缓动。不要默认为
`power2.out` 一切。良好的默认值：`power3.out`（大量入口），
`expo.out`（快速统计显示），`sine.inOut`（呼吸循环），
`elastic.out(1, 0.5)` （有趣的过度——谨慎）。

---

## 第 4 步 — 着色器过渡（最多 2–3）

在场景边界使用 HyperFrames 的内置着色器块。按心情选择：

| 着色器                     | 情绪                                  |
| -------------------------- | ------------------------------------- |
| `flash-through-white`      | 活力、乐观、流行            |
| `whip-pan`                 | 高能、体育/新闻剪辑          |
| `cinematic-zoom`           | 揭示，放大，“让我给你看” |
| `glitch`                   | 科技、前卫、故障流行                |
| `ripple-waves`             | 柔软、有机、生活方式              |
| `light-leak`               | 温暖、怀旧、电影般            |
| `cross-warp-morph`         | 平滑的场景到场景的连续性      |
| `chromatic-radial-split`   | 复古科技，VHS 美学             |
| `swirl-vortex`             | 迷失方向的梦境序列          |

其他地方都很难。一个好的规则：着色器在开始，着色器在
高潮，着色器结束。再多一点就是过度装饰了。

---

## 步骤 5 — 自我批评（开放设计的 5 暗门）

在发出 `<artifact>` 之前，给自己打 1-5 分：

- **理念**——视觉立场是否与简介和内容一致？
  活动 DS，还是通用的？
- **层次结构** — 每个场景是否都有一个主导元素？是
  阅读顺序明显吗？
- **细节** - 着色器/缓动/持续时间是否符合心情，或者它们是否
  违约？
- **功能**——引擎寻道时时间线播放是否流畅？
  所有场景 `data-start` 都是平铺的吗？ `data-duration` 总数是否匹配？
- **创新** — 是否至少有一个时刻不会出现在
  通用AI渲染？

任何低于 3/5 的值都是回归——修复并重新评分。两次通过是正常的。

---

## 第 6 步——输出合约

在 `<artifact>` 中发出正好两个文件：

### `index.html` — 组成

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title><!-- from brief --></title>
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>
  <style>
    :root { /* bound from active DESIGN.md */ }
    html, body { margin: 0; background: var(--bg); color: var(--ink); font-family: var(--font-body); }
    #stage { position: relative; width: 100vw; aspect-ratio: 16/9; overflow: hidden; }
    .scene { position: absolute; inset: 0; opacity: 0; }
    .scene.clip { /* HyperFrames toggles visibility per playhead */ }
    .scene-content { position: absolute; inset: 0; display: grid; place-items: center; padding: 6vmin; }
    /* + per-scene overrides */
  </style>
</head>
<body>
  <div id="stage" data-composition-id="my-video" data-start="0" data-width="1920" data-height="1080" data-duration="20">
    <div class="scene clip" data-start="0"   data-duration="3" data-track-index="0">
      <div class="scene-content"><!-- scene 1 content --></div>
    </div>
    <div class="scene clip" data-start="3"   data-duration="4" data-track-index="0">
      <div class="scene-content"><!-- scene 2 content --></div>
    </div>
    <!-- ... -->
  </div>

  <script>
    const tl = gsap.timeline({ paused: true });
    // === SCENE 1 ===
    tl.from(".scene[data-start='0'] .scene-content > *", { y: 30, autoAlpha: 0, duration: 0.6, ease: "power3.out", stagger: 0.08 }, 0.2);
    // === SCENE 2 ===
    tl.from(".scene[data-start='3'] .scene-content > *", { y: 30, autoAlpha: 0, duration: 0.6, ease: "power3.out", stagger: 0.08 }, 3.2);
    // ...
    window.__timelines = window.__timelines || {};
    window.__timelines["my-video"] = tl;
  </script>
</body>
</html>
```

### `preview.html` — 本地预览垫片

```html
<!doctype html>
<html><head><title>Preview</title>
<style>html,body{margin:0;background:#111;color:#eee;font:14px ui-sans-serif} iframe{border:0;width:100vw;height:100vh}</style>
</head><body>
<iframe id="f" src="index.html"></iframe>
<script>
  const f = document.getElementById('f');
  // Forward HyperFrames preview tokens (frame=, paused=, …) into the iframe
  const u = new URL('index.html', location.href);
  for (const [k,v] of new URL(location.href).searchParams) u.searchParams.set(k, v);
  f.src = u.toString();
</script>
</body></html>
```

将这两个文件保存到项目的 `cwd` 中（Open Design 已经设置了这个
至 `.od/projects/<id>/`)。代理可以立即运行：

```bash
npx hyperframes lint        # should pass with zero errors
npx hyperframes preview     # opens the studio
npx hyperframes render      # writes MP4
```

---

## 防 AI 溢出黑名单（HyperFrames 特定）

- **深色背景上没有紫色渐变**除非简要说明明确
  命名那个美学。
- **没有通用表情符号** — 使用内联 SVG 或 DS 提供的图标。
- **没有“快 10 倍”/“人工智能驱动”填充副本** — 写入用户的实际情况
  单词或使用诚实的占位符（`—` 或标记的灰色块）。
- **没有发明的品牌颜色** - 从活动 DS 或用户的读取
  执着，从来不是凭记忆。
- **每个场景都没有相同的卡片网格** — 至少 3 个不同的布局
  视频中的姿势。
- **没有挂钟 JS 动画** — `setTimeout`、`setInterval`、
  `requestAnimationFrame` 驱动的动画打破了确定性搜索。总体规划计划
  仅时间线。 （图书馆时钟动画，如 Anime.js、Motion One 和
  Lottie 通过 [HyperFrames 框架适配器](https://hyperframes.heygen.com/concepts/frame-adapters) 支持
  模式，但坚持 GSAP 进行初稿交接，除非简报
  需要另一个运行时。）

---

## 何时遵循克劳德设计说明

对于这些先进领域，治疗
[`claude-design-hyperframes.md`](https://github.com/heygen-com/hyperframes/blob/main/docs/guides/claude-design-hyperframes.md)
作为规范参考并逐字遵循其模式：

- 完整的骨架目录（骨架 A–D）
- 完整的着色器块插入模式
- HDR/广色域色彩处理
- 音频反应动画 (`hf-seek` + `window.__hfAudio`)
- 字幕/TTS 集成
- `hyperframes add` 注册表（50 多个块和组件）

这项技能始终专注于开放设计在发布时的需求——
结构规则、主动-`DESIGN.md` 绑定和 5 维自我批评
这是特定于 OD 的提示堆栈的。
