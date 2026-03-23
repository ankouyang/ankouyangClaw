# Day 02 - Onboard 与配置系统

## 今日目标

搞清楚 OpenClaw 第一次运行时如何初始化，配置系统如何组织，配置校验与落盘发生在哪。

## 今天要看的文件

- `src/cli/program/register.onboard.ts`
- `src/commands/onboard.ts`
- `src/commands/onboard-interactive.ts`
- `src/commands/onboard-non-interactive.ts`
- `src/commands/onboard-non-interactive/*`
- `src/config/config.ts`
- `src/config/io.ts`
- `src/config/validation.ts`
- `src/config/types.ts`

## 今天建议的阅读顺序

1. `src/cli/program/register.onboard.ts`
2. `src/commands/onboard.ts`
3. `src/commands/onboard-interactive.ts`
4. `src/commands/onboard-non-interactive.ts` 和子目录
5. `src/config/config.ts`
6. `src/config/io.ts`
7. `src/config/validation.ts`

## 今天必须回答的问题

1. `openclaw onboard` 到底做了哪些事情？
2. 交互式与非交互式 setup 分别走哪条路径？
3. 哪些配置是系统最小启动集？
4. 配置文件是如何读取、校验、迁移、写回的？
5. 为什么配置系统在 OpenClaw 里比普通项目更重要？

## 你应该重点观察什么

- `setupWizardCommand` 是怎样组织整个初始化流程的
- `config.ts` 只是导出层，还是真正逻辑层
- 配置 schema 是如何分模块组织的
- 重置逻辑、风险确认、运行时检查都在哪些位置做

## 今天建议产出

- 列一份 “OpenClaw 可启动的最小配置清单”
- 画一张 “onboard -> config validate -> persist” 的图
- 写一段总结：如果要做企业版一键初始化，应该从哪几层入手

## 今天不要做什么

- 不要尝试看完所有 `src/config/*`
- 不要深入某个 provider 的认证细节
- 不要扩散到 Gateway 装配逻辑

## 读完之后你应该得到的结论

- Onboard 是环境编排器，不是普通安装向导
- 配置系统是 OpenClaw 的运行规则中心
- 后续做定制化时，很多需求最终都会落到 config + onboard
