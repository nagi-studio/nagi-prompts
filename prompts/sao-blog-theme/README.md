# SAO personal blog theme

一份用于生成完整 SAO 游戏系统风格个人博客主题的实现型 Prompt。

它不是单张首页概念图提示词，而是覆盖以下页面与状态：

- 桌面端首页与移动端首页
- 游戏式主菜单、子菜单、Quick Stats 与 Message
- Quest 文章归档
- 长文章阅读页与专注阅读模式
- Skills、Items、Trace、Map、Graph 等内容页面
- 亮色、暗色、响应式和 reduced-motion
- 可选的 3D / VR 环形窗口模式

## Reference result

- Public site: https://blog.nagi.fun/
- Quest archive: https://blog.nagi.fun/blog?lang=en
- Source code: private and intentionally not included

## Use

将 [`prompt.zh-CN.md`](prompt.zh-CN.md) 完整交给代码生成 Agent。若目标项目已经存在，最好同时让 Agent 读取该项目的真实组件、数据结构和技术栈；Prompt 要求保留功能，只重建表现层。

建议分两轮执行：

1. 先完成设计 token、App Shell、菜单、首页和一个文章页。
2. 通过桌面与移动截图确认方向后，再扩展到全部内容页面和 VR 模式。

## Scope boundary

本案例公开的是设计意图和实现 Prompt，不公开原博客源码。SAO 名称、角色、字体与界面素材可能涉及第三方权利；用于独立项目时应替换为自有品牌和有权使用的素材。

