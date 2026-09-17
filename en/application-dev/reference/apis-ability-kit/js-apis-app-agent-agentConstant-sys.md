# @ohos.app.agent.agentConstant (Agent Constants) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangxuguang-huawei-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79ff6b5cab3530f52af035cd9f5c5b50875571fe translatedAt=2026-09-03T10:41:23.026Z pushedAt=2026-09-08T08:07:38.640Z -->

This module provides constants related to Agent.

**Since:** 26.0.0

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.app.agent.agentConstant (Agent Constants)](js-apis-app-agent-agentConstant.md).

## Modules to Import

```ts
import { agentConstant } from '@kit.AbilityKit';
```

## agentConstant.AgentCardType

Enumerates the types of Agent cards.

**Atomic service API**: This enum can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

| Name      | Value   | Description                   |
| --------- | ---- | ---------------------- |
| LOW_CODE  | 2    | A low-code Agent card, available only to system applications. It is suitable for the agent capabilities provided by system applications for quick construction and deployment. It supports quickly creating an agent through visual configuration or simple scripts without writing complete code, lowering the development threshold for agents.     |