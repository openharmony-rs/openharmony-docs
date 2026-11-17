# @ohos.app.ability.InsightIntentContext (Intent Execution Context) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-14T08:07:09.616Z pushedAt=2026-11-14T08:13:12.733Z nl=1 -->

This module provides the intent execution context, which is an attribute of the [intent execution base class](js-apis-app-ability-insightIntentExecutor.md) and the [intent execution base class of @InsightIntentEntry](js-apis-app-ability-InsightIntentEntryExecutor.md). It provides basic capabilities for intent execution, for example, starting a [UIAbility](js-apis-app-ability-uiAbility.md) component in the current application.

**Since:** 26.1.0

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.app.ability.InsightIntentContext (Intent Execution Context)](js-apis-app-ability-insightIntentContext.md).

## Modules to Import

```ts
import { InsightIntentContext } from '@kit.AbilityKit';
```

## Properties

**Since:** 26.1.0

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| toolCallId | string | Yes | Yes | Tool call ID passed in by the caller, used to associate this intent execution with the caller's maintenance and testing steps. When the caller does not pass in a tool call ID or passes in an empty string, the value of this property is undefined. |
