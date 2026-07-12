# NAGI Prompts

Hand-written prompts and design briefs from NAGI STUDIO.

这里公开的是可以复用、修改和继续讨论的提示词，而不是对应产品的私有源代码。每个案例尽量同时记录设计目标、效果截图、使用方式和已知限制，让 Prompt 本身包含完成作品所需的判断。

## Prompt gallery

| Prompt | Category | Preview | Language |
| --- | --- | --- | --- |
| [SAO personal blog theme](prompts/sao-blog-theme/) | Web design / frontend | [Screenshot](assets/sao-blog-theme/desktop-vr-overview.webp) | 中文 |

## Repository structure

```text
prompts/
  <prompt-slug>/
    README.md          # 案例说明和使用方法
    prompt.zh-CN.md    # 可直接复制的提示词
    meta.yaml          # 机器可读元数据
    references.md      # 截图来源与权利边界
assets/
  <prompt-slug>/       # 经检查后公开的效果截图
```

## What belongs here

- 可以独立使用的完整 Prompt，而不是只有一句灵感。
- 能说明实际效果的、经过检查的截图。
- 不泄露私有源码、密钥、内部路径或用户数据的参考截图。
- 对结果有影响的上下文、约束、失败模式和验收标准。
- 必要的版权、商标和第三方素材说明。

## What does not belong here

- 私有项目源码或可以间接还原私有实现的代码片段。
- 私有仓库地址、内部部署信息、访问令牌和账号数据。
- 未经许可转载的设计源文件或第三方素材包。
- 只有效果图、没有可复用 Prompt 的展示项目。
- 必须依赖外部页面才能成立、没有写出实际设计判断的 Prompt。

## Contributing

欢迎提交完整案例。请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。提交者需要确认 Prompt 是自己有权公开的内容，并明确参考截图及第三方素材的许可边界。

## License

除各案例另有说明外，仓库中的文字与 Prompt 使用 [CC BY 4.0](LICENSE.md) 许可。截图、商标、角色形象和第三方素材不自动包含在该许可中。
