# Day 04 - 路由与会话系统

## 今日目标

搞清楚一条消息如何被定位到 agent、account、session，以及为什么这是 OpenClaw 最关键的业务抽象之一。

## 今天要看的文件

- `src/routing/resolve-route.ts`
- `src/routing/session-key.ts`
- `src/routing/account-lookup.ts`
- `src/routing/bindings.ts`
- `src/config/sessions.ts`
- `src/config/sessions/*`
- `src/gateway/sessions-patch.ts`

## 今天建议的阅读顺序

1. `src/routing/session-key.ts`
2. `src/routing/resolve-route.ts`
3. `src/routing/account-lookup.ts`
4. `src/routing/bindings.ts`
5. `src/config/sessions.ts`
6. `src/config/sessions/*`
7. `src/gateway/sessions-patch.ts`

## 今天必须回答的问题

1. `sessionKey` 是怎么生成的？
2. `mainSessionKey` 和普通 `sessionKey` 的区别是什么？
3. route 匹配时会考虑哪些维度？
4. 为什么 OpenClaw 需要 account、peer、guild、team、role 这些维度？
5. session 状态有哪些是可 patch 的？为什么？

## 你应该重点观察什么

- route 结果结构里有哪些关键字段
- 缓存和归一化在这里扮演什么角色
- 绑定规则如何影响 session 归属
- session store 是不是 UI、CLI、channel 共用的状态源

## 今天建议产出

- 画一张 “消息 -> resolve route -> session key” 图
- 写出你自己的 session 设计理解
- 列一份 “未来做定制化时可能会碰 session 的场景清单”

## 今天不要做什么

- 不要直接跳到 agent 执行细节
- 不要扩展到所有 channel 特例
- 不要把 session 仅理解成聊天记录文件

## 读完之后你应该得到的结论

- OpenClaw 的路由系统比普通聊天项目复杂得多
- session 是业务上下文隔离的核心
- 未来新增 channel 或 agent 策略时，route 和 session 是必须理解的底层抽象
