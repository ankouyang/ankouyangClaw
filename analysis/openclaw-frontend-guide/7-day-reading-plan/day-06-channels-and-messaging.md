# Day 06 - Channels 与消息收发

## 今日目标

搞清楚 OpenClaw 如何统一管理多种消息渠道，以及消息的入站与出站是如何抽象的。

## 今天要看的文件

- `src/cli/program/register.message.ts`
- `src/cli/program/message/register.send.ts`
- `src/cli/program/message/helpers.ts`
- `src/gateway/server-channels.ts`
- `src/channels/registry.ts`
- `src/channels/plugins/*`
- 任选一个真实扩展深入，例如：
  - `extensions/telegram/*`
  - `extensions/slack/*`
  - `extensions/discord/*`

## 今天建议的阅读顺序

1. `src/cli/program/register.message.ts`
2. `src/cli/program/message/register.send.ts`
3. `src/cli/program/message/helpers.ts`
4. `src/channels/registry.ts`
5. `src/gateway/server-channels.ts`
6. 再选一个扩展包做纵向深读

## 今天必须回答的问题

1. `openclaw message send` 是如何组织参数并发出消息的？
2. channel registry 负责什么，channel runtime 负责什么？
3. 一个 `channel:account` 实例如何启动、停止、重试？
4. 入站消息和出站消息的抽象是否统一？
5. 新增一个 channel，最少要补哪些结构？

## 你应该重点观察什么

- message CLI 和 channel runtime 的边界
- registry 是元数据层还是运行层
- channel manager 如何做健康监控和 backoff
- 扩展包内部是否存在 setup、runtime、status、config 等标准结构

## 今天建议产出

- 画一张 “message send -> channel runtime -> external platform” 图
- 写一份 “新增 channel 的 checklist”
- 选定你最想模仿的一个 channel 扩展，写出它的结构模板

## 今天不要做什么

- 不要横向看太多 channel
- 不要陷入平台 SDK 细节
- 不要把 channel 仅理解为发送器

## 读完之后你应该得到的结论

- Channels 是 OpenClaw 对外连接世界的入口
- Channel manager 是统一生命周期控制器
- 做企业 IM、客服系统、Webhook 面接入时，这一天的内容最关键
