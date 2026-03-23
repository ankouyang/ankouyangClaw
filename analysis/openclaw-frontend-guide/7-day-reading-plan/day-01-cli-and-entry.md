# Day 01 - CLI 与项目入口

## 今日目标

搞清楚 OpenClaw 是如何启动的，以及为什么 CLI 是整个系统的总入口。

## 今天要看的文件

- `src/index.ts`
- `src/cli/run-main.ts`
- `src/cli/program/build-program.ts`
- `src/cli/program/command-registry.ts`
- `src/cli/program/register.subclis.ts`
- `src/cli/program/context.ts`

## 今天建议的阅读顺序

1. 先看 `src/index.ts`
2. 再看 `src/cli/run-main.ts`
3. 再看 `src/cli/program/build-program.ts`
4. 然后看 `src/cli/program/command-registry.ts`
5. 最后看 `src/cli/program/register.subclis.ts` 和 `src/cli/program/context.ts`

## 今天必须回答的问题

1. OpenClaw 真正的进程入口在哪里？
2. `runCli` 做了哪些初始化工作？
3. 为什么命令不是一次性全部注册，而是按需注册？
4. 内建命令和插件命令是怎么并存的？
5. `program context` 在这里承担什么作用？

## 你应该重点观察什么

- 启动参数如何被整理
- 根命令如何分发到子命令
- 为什么有 help fast path 和 route fast path
- 命令注册和运行逻辑是否解耦

## 今天建议产出

- 画一张 “CLI 启动 -> buildProgram -> register commands -> parseAsync” 的流程图
- 用你自己的话写 200 字总结：为什么 OpenClaw 把 CLI 设计成控制入口

## 今天不要做什么

- 不要深入每个命令的实现细节
- 不要看测试文件
- 不要扩散到 `src/gateway/*`

## 读完之后你应该得到的结论

- CLI 不是辅助工具，而是系统入口
- OpenClaw 的命令体系是懒加载和模块化的
- 后续所有阅读都可以从命令入口反推到核心实现
