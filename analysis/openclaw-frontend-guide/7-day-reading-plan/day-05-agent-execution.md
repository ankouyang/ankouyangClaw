# Day 05 - Agent 执行主链

## 今日目标

搞清楚 `openclaw agent` 这条链是怎么从 CLI 进入 Gateway，再到 agent runtime，最后返回结果的。

## 今天要看的文件

- `src/cli/program/register.agent.ts`
- `src/commands/agent-via-gateway.ts`
- `src/commands/agent.ts`
- `src/commands/agent/session.ts`
- `src/gateway/call.ts`
- `src/agents/*`

## 今天建议的阅读顺序

1. `src/cli/program/register.agent.ts`
2. `src/commands/agent-via-gateway.ts`
3. `src/gateway/call.ts`
4. `src/commands/agent.ts`
5. `src/commands/agent/session.ts`
6. 再按需看 `src/agents/*` 的关键文件

## 今天必须回答的问题

1. `openclaw agent --message` 的执行入口是什么？
2. 什么时候通过 Gateway 执行，什么时候 fallback 到 embedded？
3. agent 请求里哪些参数会影响行为？
4. `idempotencyKey`、`sessionKey`、`thinking`、`deliver` 分别控制什么？
5. agent runtime 为什么不是简单的模型调用？

## 你应该重点观察什么

- CLI 如何构造 agent 请求
- Gateway 调用与本地 fallback 的分支
- session 是如何绑定到 agent 执行的
- agent 的结果是纯文本，还是 payload 结构

## 今天建议产出

- 画一张 “agent 命令执行链路图”
- 用自己的话写一段：agent 和 message send 的根本区别是什么
- 列一个清单：如果以后你要做企业工作流 agent，最可能改哪些层

## 今天不要做什么

- 不要试图一次看完整个 `src/agents/*`
- 不要展开到所有工具实现
- 不要过度陷入 provider 细节

## 读完之后你应该得到的结论

- OpenClaw 的 agent 是带 session、路由、投递策略的执行系统
- CLI 只是触发器，核心调度在 Gateway
- 未来你做自动化、工作流、子代理时，主要会落在这条链上
