# @ohos.app.ability.scriptManager (Script Management) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @RuiChen_01-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=192d5f6c23423351aaca48bfe8c34ca273119670 translatedAt=2026-11-04T09:51:33.795Z pushedAt=2026-11-04T09:53:31.440Z nl=1 -->

This module provides the capability to manage and organize script information, and supports reporting the execution results of ArkTS scripts in an app.

**Since:** 26.0.1

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.app.ability.scriptManager (Script Management)](js-apis-app-ability-scriptManager.md).

## Modules to Import

```ts
import { scriptManager } from '@kit.AbilityKit';
```

## ArkTSScriptInfo

The first parameter of the ArkTS script entry function of an app, used to receive the script context information passed by the system.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| toolCallId | string | Yes | Yes | Tool call ID passed in by the caller, used to associate this ArkTS script call with the caller's maintenance and testing steps. When the caller does not pass in a tool call ID or passes in an empty string, the value of this property is undefined.|
