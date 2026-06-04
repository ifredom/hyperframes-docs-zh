<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/logo/dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="docs/logo/light.svg">
    <img alt="HyperFrames" src="docs/logo/light.svg" width="300">
  </picture>
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/hyperframes"><img src="https://img.shields.io/npm/v/hyperframes.svg?style=flat" alt="npm版本"></a>
  <a href="https://www.npmjs.com/package/hyperframes"><img src="https://img.shields.io/npm/dm/hyperframes.svg?style=flat" alt="npm 下载"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue.svg" alt="执照"></a>
  <a href="https://nodejs.org"><img src="https://img.shields.io/badge/node-%3E%3D22-brightgreen" alt="Node.js"></a>
  <a href="https://discord.gg/EbK98HBPdk"><img src="https://img.shields.io/badge/Discord-Join-5865F2?logo=discord&logoColor=white" alt="Discord"></a>
</p>

<p align="center"><b>编写 HTML。渲染视频。专为智能体打造。</b></p>

<p align="center">
  <a href="https://hyperframes.heygen.com/quickstart">快速入门</a> |
  <a href="https://hyperframes.heygen.com/showcase">展示</a> |
  <a href="https://www.hyperframes.dev/">游乐场</a> |
  <a href="https://hyperframes.heygen.com/catalog/blocks/data-chart">目录</a> |
  <a href="https://hyperframes.heygen.com/introduction">文档</a> |
  <a href="https://discord.gg/EbK98HBPdk">Discord</a>
</p>

<p align="center">
  <img src="https://static.heygen.ai/hyperframes-oss/docs/images/hfgif-1280.webp" alt="HyperFrames 演示：左侧的 HTML 代码转换为右侧的渲染视频" width="800">
</p>

HyperFrames 是一个开源框架，用于将 HTML、CSS、媒体和可寻址动画转换为确定性 MP4 视频。通过 CLI 在本地使用它，通过具有技能的 AI 编码智能体，或作为托管创作工作流程背后的渲染核心。

## 快速入门

### 使用AI 编码智能体

安装 HyperFrames 技能，然后描述您想要的视频：

```bash
npx skills add heygen-com/hyperframes
```

尝试使用如下提示：

> 使用 `/hyperframes` 创建一个 10 秒的产品介绍，其中包含淡入标题、背景视频和微妙的背景音乐。

这些技能向代理教授 HyperFrames 制作循环：规划视频、编写有效的 HTML、连接可寻址动画、添加媒体、lint、预览和渲染。他们与 Claude Code、Cursor、Gemini CLI、Codex 和其他支持技能的编码代理一起工作。

有关视觉设计移交工作流程，请参阅 [Claude 设计指南](https://hyperframes.heygen.com/guides/claude-design) 和 [开放设计指南](https://hyperframes.heygen.com/guides/open-design)。

### 使用 CLI 手动

```bash
npx hyperframes init my-video
cd my-video
npx hyperframes preview      # preview in browser with live reload
npx hyperframes render       # render to MP4
```

**要求：** Node.js 22+、FFmpeg

## 您可以构建什么

需要想法吗？浏览[展示](https://hyperframes.heygen.com/showcase)，查看您可以观看、阅读、运行和重新混合的成品视频。

- 产品发布视频和功能公告
- 包含动画代码差异、旁白和标题的 PR 演练
- 数据可视化、图表竞赛和地图动画
- 带有动态字幕、叠加层和音乐的社交视频
- 文档到视频、PDF 到视频和网站到视频讲解器
- 用于自动化内容管道的可重复使用的动态图形

## frame.md

**frame.md — 您的设计系统，准备好播放视频。**

每个品牌都有一个 `design.md`。它们都不是为相机而写的。 `frame.md` 是缺少的翻译层：它采用您的网络上下文设计规范并将其反转为框架 - 相同的标记，相同的规则，但经过重写，以便人工智能代理可以编写宣传视频，而无需猜测比例或达到网络镶边。

输出是整个工具链可以读取的 `DESIGN.md` 超集。原子保持神圣。构图保持自由。数字来自脚本。

<table>
  <tr>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/biennale-yellow"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/biennale-yellow.png" alt="双年展黄" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/biennale-yellow">双年展黄</a></b>
    </td>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/blockframe"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/blockframe.png" alt="块框架" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/blockframe">块框架</a></b>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/blue-professional"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/blue-professional.png" alt="蓝色专业" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/blue-professional">蓝色专业</a></b>
    </td>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/bold-poster"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/bold-poster.png" alt="大胆的海报" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/bold-poster">大胆的海报</a></b>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/broadside"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/broadside.png" alt="宽边" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/broadside">宽边</a></b>
    </td>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/capsule"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/capsule.png" alt="胶囊" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/capsule">胶囊</a></b>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/cartesian"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/cartesian.png" alt="笛卡尔" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/cartesian">笛卡尔</a></b>
    </td>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/cobalt-grid"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/cobalt-grid.png" alt="钴网格" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/cobalt-grid">钴网格</a></b>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/coral"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/coral.png" alt="珊瑚" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/coral">珊瑚</a></b>
    </td>
    <td width="50%" align="center">
      <a href="https://www.hyperframes.dev/design/creative-mode"><img src="https://static.heygen.ai/hyperframes-oss/docs/images/design-templates/creative-mode.png" alt="创意模式" width="100%"></a>
      <br><b><a href="https://www.hyperframes.dev/design/creative-mode">创意模式</a></b>
    </td>
  </tr>
</table>

在 [hyperframes.dev/design](https://www.hyperframes.dev/design) 中浏览并重新混合它们。

## 它是如何运作的

将视频定义为 HTML。添加计时和轨道的数据属性。使用 GSAP、CSS、Lottie、Three.js、Anime.js、WAAPI 或您自己的帧适配器来实现可寻址动画。

```html
<div id="stage" data-composition-id="launch" data-start="0" data-width="1920" data-height="1080">
  <video
    class="clip"
    data-start="0"
    data-duration="6"
    data-track-index="0"
    src="intro.mp4"
    muted
    playsinline
  ></video>

  <h1 id="title" class="clip" data-start="1" data-duration="4" data-track-index="1">Launch day</h1>

  <audio
    data-start="0"
    data-duration="6"
    data-track-index="2"
    data-volume="0.5"
    src="music.wav"
  ></audio>

  <script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
  <script>
    const tl = gsap.timeline({ paused: true });
    tl.from("#title", { opacity: 0, y: 40, duration: 0.8 }, 1);
    window.__timelines = window.__timelines || {};
    window.__timelines.launch = tl;
  </script>
</div>
```

在浏览器中立即预览。在本地或 Docker 中渲染。渲染器在无头 Chrome 中查找每个帧并使用 FFmpeg 对结果进行编码，因此相同的输入会生成相同的视频。

## HyperFrames堆栈

HyperFrames 是开源渲染引擎，还有一组不断增长的围绕 HTML 原生视频创建的工具。

| 片                                           | 地位              | 它的作用                                                                                      |
| ----------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------- |
| 命令行界面                                             | 可用的           | 支架、预览、lint、检查和渲染本地视频项目                                 |
| 核心/引擎/制作人                        | 可用的           | 解析合成、驱动无头 Chrome、编码视频和混合音频                            |
| 目录                                         | 可用的           | 可重复使用的块和组件，用于过渡、叠加、标题、图表、地图和效果     |
| 代理技巧                                    | 可用的           | 向编码代理传授一般网络文档所忽略的视频制作模式                      |
| 工作室                                          | 可用，不断发展 | 用于预览和编辑合成的浏览器界面                                           |
| AWS Lambda 渲染                            | 可用的           | 部署分布式渲染堆栈并从笔记本电脑或 CI 驱动渲染                        |
| [hyperframes.dev](https://www.hyperframes.dev/) | 可用的           | 用于预览、迭代、共享和渲染 HTML 原生视频项目的社区游乐场 |
| [frame.md](https://www.hyperframes.dev/design)  | 可用的           | 反转相机的设计系统 - 一个 DESIGN.md 超集，代理可以从中编写视频   |

## 目录

安装即用型块和组件：

```bash
npx hyperframes add flash-through-white   # shader transition
npx hyperframes add instagram-follow      # social overlay
npx hyperframes add data-chart            # animated chart
```

浏览 [hyperframes.heygen.com/catalog](https://hyperframes.heygen.com/catalog/blocks/data-chart) 上的目录。

## 为什么选择HyperFrames？

- **HTML-native：**组合物是具有数据属性的 HTML 文件。没有 React 要求，没有专有的时间线格式。
- **代理友好：**代理已经编写了 HTML，并且 CLI 默认情况下是非交互式的。
- **确定性：**相同的输入，相同的帧，相同的输出。专为 CI、回归测试和自动渲染而构建。
- **无构建步骤：** `index.html` 作品按原样播放，并且可以直接在浏览器中预览。
- **基于适配器的动画：**带来 GSAP、CSS 动画、Lottie、Three.js、Anime.js、WAAPI 或自定义运行时。
- **开源：** Apache 2.0 许可证，无每次渲染费用或商业使用门槛。

## HyperFrames与远程

HyperFrames 的灵感来自于 [Remotion](https://www.remotion.dev)。这两个工具都使用无头 Chrome 和 FFmpeg 渲染视频。主要区别在于创作模型：Remotion 的赌注是 React 组件； HyperFrames 的赌注是人类和代理都可以轻松编写的纯 HTML。

|                          | **超级框架**                       | **远程**                            |
| ------------------------ | ------------------------------------- | --------------------------------------- |
| 创作                | HTML + CSS + 可寻址动画       | 反应组件                        |
| 构建步骤               | 没有任何; `index.html` 按原样播放        | 需要捆绑器                        |
| 座席切换            | 纯 HTML 文件                      | JSX / React 项目                     |
| 图书馆时钟动画 | 通过适配器可搜索、帧精确 | 挂钟动画图案需要小心 |
| 分布式渲染    | 本地和 AWS Lambda 渲染路径     | Remotion Lambda，成熟的云渲染器  |
| 执照                  | 阿帕奇2.0                            | 可用源远程许可证       |

请阅读 [HyperFrames 与 Remotion 指南](https://hyperframes.heygen.com/guides/hyperframes-vs-remotion) 中的完整比较。

## 文档

完整文档：[hyperframes.heygen.com/introduction](https://hyperframes.heygen.com/introduction)

- [快速入门](https://hyperframes.heygen.com/quickstart)
- [展示](https://hyperframes.heygen.com/showcase)
- [指南](https://hyperframes.heygen.com/guides/gsap-animation)
- [API参考](https://hyperframes.heygen.com/packages/core)
- [目录](https://hyperframes.heygen.com/catalog/blocks/data-chart)
- [示例](https://hyperframes.heygen.com/examples)
- [AWS Lambda 渲染](https://hyperframes.heygen.com/deploy/aws-lambda)

## 套餐

| 包裹                                                          | 描述                                                       |
| ---------------------------------------------------------------- | ----------------------------------------------------------------- |
| [`hyperframes`]（包/cli）                                    | 用于创建、预览、检查和渲染合成的 CLI |
| [`@hyperframes/core`]（包/核心）                             | 类型、解析器、生成器、linter、运行时和框架适配器   |
| [`@hyperframes/engine`]（包/引擎）                         | 使用 Puppeteer 和 FFmpeg 的可搜索页面到视频捕获引擎  |
| [`@hyperframes/producer`]（包/生产者）                     | 用于捕获、编码和音频混合的完整渲染管道        |
| [`@hyperframes/studio`]（包/工作室）                         | 基于浏览器的合成编辑器 UI                               |
| [`@hyperframes/player`]（包/玩家）                         | 可嵌入 `<hyperframes-player>` Web 组件                   |
| [`@hyperframes/shader-transitions`]（包/着色器过渡） | 合成的 WebGL 着色器过渡                         |
| [`@hyperframes/aws-lambda`]（包/aws-lambda）                 | 用于分布式渲染的 AWS Lambda SDK 和部署界面     |

## 社区

HyperFrames 在 [HeyGen](https://www.heygen.com) 的生产中使用，社区示例来自 [tldraw](https://tldraw.com)、[TanStack](https://tanstack.com) 等团队，以及 [ADOPTERS.md](ADOPTERS.md) 中的其他团队。如果您的团队正在使用 HyperFrames，请打开 PR。

- 问题和想法：[Discord](https://discord.gg/EbK98HBPdk)
- 错误和功能请求：[GitHub 问题](https://github.com/heygen-com/hyperframes/issues)
- 安全报告：[SECURITY.md](SECURITY.md)
- 贡献：[CONTRIBUTING.md](CONTRIBUTING.md)

## 开发笔记

该存储库使用 [Git LFS](https://git-lfs.com) 作为 `packages/producer/tests/**/output.mp4` 下的黄金回归测试基线（大约 240 MB 的 `.mp4` 文件）。如果您要克隆完整的存储库进行开发，请先安装 Git LFS：

```bash
# macOS
brew install git-lfs

# Ubuntu / Debian
sudo apt install git-lfs

# Windows
winget install GitHub.GitLFS

# Then, once per machine
git lfs install
```

如果只需要源文件，可以跳过LFS内容：

```bash
GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/heygen-com/hyperframes.git
```

## 执照

[Apache 2.0]（许可证）
