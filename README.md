# NAGI Prompts

Open prompts behind NAGI STUDIO ideas and experiments.

这里公开的是可以复用、修改和继续讨论的提示词，而不是对应产品的私有源代码。每个案例尽量同时记录设计目标、公开成品、参考截图、使用方式和已知限制，让提示词不脱离真实结果单独存在。

## Prompt gallery

| Prompt | Category | Reference | Language |
| --- | --- | --- | --- |
| [SAO personal blog theme](prompts/sao-blog-theme/) | Web design / frontend | [blog.nagi.fun](https://blog.nagi.fun/) | 中文 |

## Repository structure

```text
prompts/
  <prompt-slug>/
    README.md          # 案例说明和使用方法
    prompt.zh-CN.md    # 可直接复制的提示词
    meta.yaml          # 机器可读元数据
    references.md      # 公开成品、截图与来源边界
assets/
  <prompt-slug>/       # 经检查后公开的效果截图
```

## What belongs here

- 可以独立使用的完整 Prompt，而不是只有一句灵感。
- Prompt 对应的公开成品链接。
- 不泄露私有源码、密钥、内部路径或用户数据的参考截图。
- 对结果有影响的上下文、约束、失败模式和验收标准。
- 必要的版权、商标和第三方素材说明。

## What does not belong here

- 私有项目源码或可以间接还原私有实现的代码片段。
- 私有仓库地址、内部部署信息、访问令牌和账号数据。
- 未经许可转载的设计源文件或第三方素材包。
- 只有效果图、没有可复用 Prompt 的展示项目。

## Contributing

欢迎提交完整案例。请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。提交者需要确认 Prompt 是自己有权公开的内容，并明确参考截图及第三方素材的许可边界。

## License

除各案例另有说明外，仓库中的文字与 Prompt 使用 [CC BY 4.0](LICENSE.md) 许可。截图、商标、角色形象和第三方素材不自动包含在该许可中。

