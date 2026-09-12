# @ohos.app.agent.agentConstant (Agent Constants)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangxuguang-huawei-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T10:42:35.427Z pushedAt=2026-09-05T10:47:30.469Z -->

The agentConstant module provides Agent-related constants, including the Agent card type [AgentCardType](#agentconstantagentcardtype), which is used to identify and distinguish the type of an Agent card when calling Agent-related APIs (such as agentManager).

**Since:** 26.0.0

## Modules to Import

```ts
import { agentConstant } from '@kit.AbilityKit';
```

## agentConstant.AgentCardType

Enumerates the types of Agent cards.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This enum can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name      | Value   | Description                   |
| --------- | ---- | ---------------------- |
| APP       | 0    | Application-type Agent card, applicable to traditional installed applications. The Agent capability is installed and uninstalled along with the application, and the user must install the application before using it.  |
| ATOMIC_SERVICE | 1 | Atomic-service-type Agent card, applicable to installation-free atomic services. The Agent capability can be used on demand without pre-installation, supporting quick experience and sharing. |