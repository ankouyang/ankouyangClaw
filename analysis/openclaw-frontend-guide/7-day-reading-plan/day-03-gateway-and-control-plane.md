# Day 03 - Gateway 与控制面

## 今日目标

搞清楚 Gateway 为什么是 OpenClaw 的核心，以及 Gateway 启动时究竟装配了哪些系统能力。

## 今天要看的文件

- `src/cli/gateway-cli/register.ts`
- `src/cli/gateway-cli/run.ts`
- `src/gateway/server.impl.ts`
- `src/gateway/server-runtime-config.ts`
- `src/gateway/server-runtime-state.ts`
- `src/gateway/server-http.ts`
- `src/gateway/server-methods-list.ts`
- `src/gateway/server-startup-log.ts`

## 今天建议的阅读顺序

1. `src/cli/gateway-cli/register.ts`
2. `src/cli/gateway-cli/run.ts`
3. `src/gateway/server.impl.ts`
4. `src/gateway/server-runtime-config.ts`
5. `src/gateway/server-runtime-state.ts`
6. `src/gateway/server-http.ts`
7. `src/gateway/server-methods-list.ts`

## 今天必须回答的问题

1. Gateway 为什么是控制面，而不是普通 API 服务？
2. `openclaw gateway run` 最终是怎么走到 `server.impl.ts` 的？
3. Gateway 启动时装配了哪些关键子系统？
4. HTTP 和 WebSocket 在 OpenClaw 里分别承担什么角色？
5. 哪些状态由 Gateway 统一持有和协调？

## 你应该重点观察什么

- `server.impl.ts` 里有哪些“系统级组装”动作
- runtime config 和 runtime state 是如何分工的
- Gateway 方法表是如何组织的
- 控制面是否围绕 session、channel、plugin、node 四类能力展开

## 今天建议产出

- 画一张 “Gateway 启动装配图”
- 列一张 Gateway 子系统清单：config、channels、auth、cron、plugins、health、nodes
- 用自己的话写清楚：为什么说 OpenClaw 是 Gateway-first 架构

## 今天不要做什么

- 不要深入每一个 method handler
- 不要急着看 UI
- 不要扩散到 channel 插件内部实现

## 读完之后你应该得到的结论

- Gateway 是系统主脑
- OpenClaw 的很多能力都不是直接挂在 CLI，而是统一挂在 Gateway
- 以后做任何扩展，都要先判断自己改的是 CLI 层、Gateway 层还是 plugin 层
