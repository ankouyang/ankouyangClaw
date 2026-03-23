# Day 07 - 插件体系、UI 与扩展路线

## 今日目标

搞清楚 OpenClaw 的扩展边界在哪里，以及你未来应该优先从哪一层做项目化定制。

## 今天要看的文件

- `src/plugins/runtime/index.ts`
- `src/plugins/loader.ts`
- `src/plugins/registry.ts`
- `src/plugins/cli.ts`
- `src/plugins/runtime/*`
- `ui/src/ui/*`
- `ui/src/ui/gateway.ts`
- `ui/src/ui/presenter.ts`
- 再选一个扩展包深入，例如：
  - `extensions/openai/*`
  - `extensions/firecrawl/*`
  - `extensions/msteams/*`

## 今天建议的阅读顺序

1. `src/plugins/runtime/index.ts`
2. `src/plugins/registry.ts`
3. `src/plugins/loader.ts`
4. `src/plugins/runtime/*`
5. `ui/src/ui/gateway.ts`
6. `ui/src/ui/presenter.ts`
7. `ui/src/ui/*`
8. 选一个扩展包纵向阅读

## 今天必须回答的问题

1. plugin runtime 暴露了哪些稳定能力？
2. 为什么 OpenClaw 强调通过 runtime 而不是直接 import core 内部实现？
3. plugin loader 和 registry 分别负责什么？
4. Web UI 是怎么连接 Gateway 的？
5. 如果要做项目化扩展，优先应该改 provider、tool、channel、UI 还是 core？

## 你应该重点观察什么

- runtime 是否像平台 SDK
- plugin runtime 的子能力如何拆分
- UI 是状态消费层还是业务主导层
- 扩展包是否遵守统一 contract

## 今天建议产出

- 写一份 “我的第一批扩展方向” 文档
- 至少选一个方向明确落点：
  - 自定义 provider
  - 自定义 tool
  - 自定义 channel
  - Control UI 定制
- 列出每个方向对应的核心文件入口

## 今天不要做什么

- 不要继续泛读所有扩展包
- 不要一上来直接动 core
- 不要把 UI 当成整个系统中心

## 读完之后你应该得到的结论

- OpenClaw 的正确扩展姿势是优先走插件边界
- UI 是控制面的一部分，但不是唯一主角
- 7 天结束后，你应该已经能判断自己的定制需求该落到哪一层
