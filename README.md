# NAGI Prompts

> Open ideas, not source code.

这里公开 NAGI STUDIO 项目背后的想法和完整 Prompt，但不公开对应项目的源代码。

每个项目只保留两样东西：一张展示实际效果的图片，以及一份可以独立阅读的完整 Prompt。新增项目时，继续在这个 README 底部追加新的章节。

## Projects

- [SAO Personal Blog Theme](#sao-personal-blog-theme)

---

## SAO Personal Blog Theme

![SAO personal blog theme](assets/sao-blog-theme.webp)

### Prompt

```text
# 复刻完整 SAO 个人博客主题

你是一名高级前端工程师和 UI 系统设计师。请实现一套可用于完整个人博客的主题，准确复刻一个以《刀剑神域》游戏系统界面为核心的个人数字花园。

这不是重新设计，也不是“参考后自由发挥”。目标是高保真复刻既有主题的视觉骨架、组件语言、响应式布局和沉浸式交互，同时允许替换博客内容、作者资料和数据。

## 一、主题定位

将整个博客表现为 Sword Art Online 世界中的游戏系统界面：

- 用户不是在浏览普通网站，而是在操作 Aincrad 世界里的个人档案、任务日志、技能、物品和轨迹系统。
- 使用 diegetic UI：导航、文章、统计、地图、设置都像游戏世界内真实存在的系统窗口。
- 视觉关键词：SAO system UI、Aincrad、frosted hologram window、amber system accent、warm sand world、personal digital garden、quest log、inventory、player status。
- 气质轻盈、安静、略带怀旧和仪式感。
- 不能做成通用赛博朋克、霓虹电竞后台、紫蓝 AI 渐变网站或传统三栏博客。

如果现有项目已经包含功能和数据，不得破坏、删除或重写业务逻辑。先抽取主题 token 和可复用组件，再逐步替换表现层。

## 二、技术与组件

沿用目标项目已有技术栈。如果从零实现，使用 SvelteKit、Svelte 5、TypeScript 和 SCSS/CSS Variables；使用 GSAP 负责编排型动画；Three.js 或 Threlte 只用于可选的 VR/3D 环形窗口模式。

至少建立这些组件：

- AppShell
- SAOWindow / SAOPanel
- SAOMenu / ProfileCard
- QuickStats / MessagePanel
- FloatingNav / MobileNav
- StatusHUD / HPBar / SessionClock
- ArticleCard / ActivityCard / TagFilter
- ArticleReader / TableOfContents / KnowledgeGraphPanel
- ModalPanel / ThemeToggle

不要在每个页面重复硬编码样式。

## 三、全局视觉系统

### 背景

背景固定覆盖视口。

亮色模式使用 Aincrad 沙岩色世界渐变：`#e8d5b7`、`#c9a980`、`#8b7355`、`#5a4a3a`，方向约 135deg。左上加入柔和暖橙径向光晕，右下允许极弱的淡紫环境光，并叠加稀疏、半透明、缓慢上浮的白色粒子。

暗色模式使用 Aincrad dusk：`#1c1f2e`、`#252238`、`#3a2f3f`，只保留微弱琥珀环境光。主题切换时让两层背景交叉淡入淡出。

### 色彩

- 系统主强调色：`#f5a623`
- 发光琥珀色：`#ffcc00`
- 深琥珀色：`#d48806`
- 功能蓝：`#4a90d9`
- 功能粉：`#d63384`
- HP 绿色：`#9acd32`
- 主要文字：`#4a4a4a`
- 次级文字：`#7a7a7a`

琥珀色是唯一持续出现的系统强调色。蓝、粉、绿只用于具有明确语义的状态和内容类别。

### 窗口材质

亮色窗口使用 `rgba(255,255,255,0.78)`、`backdrop-filter: blur(14px) saturate(1.3)`、1px 半透明灰色边界、12px 圆角和 `0 6px 24px rgba(0,0,0,0.12)` 阴影。

暗色窗口使用 `rgba(28,28,34,0.82)` 和 `rgba(80,80,90,0.5)` 边界。窗口顶部包含浅色渐变 header，底部有 2px 琥珀系统线；右上只保留一个低透明度圆形状态点，不模仿 macOS 三色按钮。

移动端关闭实时 backdrop blur，改用接近不透明的表面。

### 字体

- SAO UI：正文、导航、标签、数据和普通标题
- SAO Welcome：欢迎标题、窗口标题和仪式性标题
- 中文回退：Noto Sans SC
- 日文回退：Noto Sans JP
- 长文章提供 Times New Roman / Georgia / Noto Serif SC 阅读模式

正文默认 16px、line-height 1.8。中文和日文不要增加过大字间距。

## 四、桌面布局与菜单

页面最大宽度 1400px，水平居中，顶部留白约 100px。左侧是 480px 系统侧栏，中间间隔 32px，右侧是自适应主内容区。

左侧栏依次包含角色菜单、Quick Stats 和 Message。

角色菜单不是普通侧边导航：左侧为约 240px 的 Profile Card，中间为竖直排列的 36px 游戏图标，点击主图标后在右侧展开约 160px 的子菜单。

Profile Card 包含 Menu 标题、灰色人物剪影、围绕人物呼吸的圆形节点、几何折线分隔符、“The menu of my blog”和指向菜单的三角箭头。

主菜单语义：

- Status：Skills、Items、Playback
- Party：Party、Friend、Sponsor
- Memos：Quest、Memo、Trace、Graph
- Map
- System：About、Site Policy、Option、Help、Logout

使用风格一致的几何系统图标。子菜单 active 状态使用极淡琥珀背景、左侧 2px 琥珀内描边和可移动的琥珀三角指针。菜单根据 active item 平滑调整位置。

## 五、全局 HUD

- 左上：玩家姓名、Level 和 HP 状态条
- HP 条使用深色底、绿色渐变填充和斜切右端
- 右下：Session 计时器，使用 tabular numbers
- 非首页左下：40×40 返回按钮
- 可选音乐播放时显示细长音频可视化组件

HUD 必须轻量，不能抢夺正文注意力。

## 六、首页

首页上方居中显示 “Welcome to Sword Art Online !”。使用 SAO Welcome 字体，字号 `clamp(2rem, 6vw, 4rem)`，白色文字配柔和琥珀外发光和少量深色投影。保留大量留白，不添加普通营销站 CTA。

下方显示 Recent Activity / 最近動態，并附低透明度日文假名。

Recent Activity 桌面端为 2×2 网格，移动端为单列。卡片上部为图片，下部只放标题和日期。主体图使用 `object-fit: contain`；在其后复制同图、放大并 blur 24px 以填充留白，不能粗暴裁切封面。

左上角放矩形类型条：Quest 为琥珀色、Thought 为蓝色、Anime 为粉色、Skill 为绿色。Hover 时卡片上浮 2px、出现细琥珀描边，图片放大至 1.04。

## 七、列表与内容页面

列表页标题使用英文大标题、日文副标题、短 2px 琥珀线和一行低透明度系统状态文案。

文章归档命名为 Quests / クエスト。顶部提供可横向滚动的标签筛选条，标签带数量；active 状态使用淡琥珀背景、琥珀边框和文字。

文章列表使用纵向大卡片，不能做成三列等宽卡片墙。桌面卡片左侧约 420px 封面，右侧为标题、日期、阅读时长、摘要和标签。封面与正文之间有细渐变分隔线，中央带发光琥珀节点。Hover 时整卡向右移动 4px，左边缘出现 4px 琥珀状态条，封面轻微放大。当卡片容器小于约 700px 时自动改成上下布局。

其他内容集合沿用同一系统语言：

- Memos：不等高记录卡片
- Trace：照片轨迹网格
- Skills：系统技能列表
- Items：玩家 inventory，可加入稀有度、扫描线和克制的全息效果
- Playback：Anime 与 Books 收藏入口
- Graph：知识图谱嵌入 SAO 窗口
- Map：世界地图和访客链路嵌入 SAO 窗口
- About、Policy、Sponsor、Settings：统一使用 SAOWindow

## 八、文章阅读页

文章放在最大宽度约 1040–1260px 的 SAOWindow 中，窗口标题直接使用文章标题。

内容顺序：返回 Quest Log、封面、Quick Summary、作者与 Last reviewed、日期和阅读时长、标签、阅读控制、正文、Series、Backlinks、Local Graph、Article Info、许可、Reactions、Comments。

Quick Summary 使用左侧 3px 琥珀线、极淡琥珀背景和小号 uppercase 标签。

阅读控制包含：Font（SAO / Serif）、Reading（Focus）、Size（− / 百分比 / +）和 Lang（EN / 中文）。

英文正文约 75ch，中文约 42em；Focus 模式缩窄至英文 65ch、中文 38em，同时提高字号、模糊并压暗外围 UI。

正文样式：

- h1 2em、h2 1.6em、h3 1.25em
- 普通链接使用功能蓝
- 内部链接为蓝色虚线下划线，hover 时出现琥珀生长线
- blockquote 使用淡琥珀底、细边框、左侧渐隐琥珀轨道和菱形节点
- inline code 使用淡琥珀背景
- code block 使用温暖白灰或深炭色 shell，不用纯黑终端
- 表格允许横向滚动
- 顶部增加细琥珀阅读进度线

宽屏时在右侧显示独立 reading rail，包含阅读控制、可折叠目录、当前标题高亮、Local Graph、Series 和 Backlinks。

## 九、交互与动效

动效必须像系统界面组装，而不是网页元素随便飞入。

- micro feedback：150ms
- 普通 UI：300ms
- 窗口 materialize：500ms
- 仪式性动画：800ms
- 主要缓动：`cubic-bezier(0.22, 1, 0.36, 1)`

Hover 移动 2–4px 或轻微缩放；active 使用 scale 0.96–0.98。子菜单从侧面淡入并依次出现。卡片进入视口时从中间细线向上下展开，像系统窗口 materialize。

页面退出时降低透明度、向上移动 10px、scale 0.992；进入时从 y=14px、scale 0.992 复原。页面切换时增加一条从上到下扫过的琥珀 scanline。

可以加入 hover、confirm、back、achievement 音效，但必须可以关闭。全部动画遵守 `prefers-reduced-motion`。

## 十、暗色与移动端

暗色模式不能使用纯黑：背景保持炭灰、暮紫和微弱琥珀环境光；面板继续半透明；标题为暖白；琥珀发光比亮色模式更克制。默认亮色，同时支持 light / dark / system。

900px 以下隐藏桌面侧栏和 FloatingNav，主内容全宽，内边距约 16px。右上显示 50×50 圆形菜单按钮，带琥珀双环和低速旋转虚线。展开后出现遮罩，并从左侧滑出宽度 85%、最大 360px 的抽屉，依次包含 Menu、Quick Stats 和 Message。

移动端停止背景粒子，关闭实时 blur；活动卡改单列；Quest 卡改为封面在上、内容在下；保证正文和 HUD 不产生横向滚动或相互遮挡。

## 十一、可选 VR View

VR View 只能作为渐进增强。将 Menu、Stats、Message 和 Content 变成围绕用户排列的独立 3D 窗口，使用全景天空背景，并允许旋转视角。文章 rail 可以成为独立窗口。退出 VR 后恢复平面布局和滚动状态。

低性能设备、爬虫、无 WebGL 或 reduced-motion 环境自动使用平面布局。

## 十二、无障碍与性能

- 导航使用真实链接，按钮支持键盘和 Escape
- active page、focus ring、loading、empty、error 状态明确
- 图片使用正确 alt、响应式尺寸、lazy loading 和 async decoding
- 使用 main、aside、nav、article、section 等语义元素
- 不让 SSR、爬虫或无 JavaScript 页面中的卡片保持隐藏
- 移动端避免 backdrop-filter 和大面积 blur 动画
- 动画只优先操作 transform、opacity 和 clip-path
- 不允许明显 CLS 和页面级横向滚动

## 十三、禁止偏离

严格禁止：

- 通用 Tailwind/SaaS landing page
- 顶部普通 navbar + Hero + 三张功能卡
- 紫蓝 AI 渐变或纯黑赛博朋克背景
- 满屏霓虹线框
- 所有组件都做成 pill
- 每张卡片使用完全相同的边框、圆角和阴影
- 使用 emoji 代替正式图标
- 把页面命名改回 Posts、Portfolio、Dashboard
- 删除 Quest、Skills、Items、Trace、HP、Session 等世界观语义
- 为视觉效果牺牲长文章可读性
- 只复刻首页而忽略文章、归档、移动端和暗色模式

## 十四、交付标准

交付完整可运行实现，而不是静态概念稿。至少完成并验证：

- 桌面首页与移动首页
- Quest 列表
- 文章阅读页
- About 或 Settings 页面
- 亮色与暗色模式
- 桌面菜单与移动抽屉
- hover、active、focus、loading、empty 状态
- responsive layout
- prefers-reduced-motion
- 主题 token 和组件文档

开始编码前先审计现有项目，列出准备复用的组件、数据和功能。实现后运行类型检查、构建和响应式验证，并逐项对照上述要求。不要在完成一张首页截图后停止。
```

### Rights

Prompt 和文字说明可以自由学习、分享和修改，但请保留来源说明。展示图只用于说明项目效果；其中涉及的商标、字体、角色形象和第三方素材仍归各自权利人所有。
