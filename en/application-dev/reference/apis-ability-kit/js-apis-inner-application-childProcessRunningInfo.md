# ChildProcessInformation
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8930119bf73ebfc2f2829b95d93d438b219cafb2 translatedAt=2026-11-04T09:55:22.510Z pushedAt=2026-11-04T09:59:51.241Z nl=1 -->

ChildProcessInformation defines the information about a child process, including the PID of the child process, the PID of the parent process, and the name of the child process. It can be obtained through [getChildProcessInfos](js-apis-app-ability-childProcessManager.md#childprocessmanagergetchildprocessinfos) and [getUIAbilityChildProcessInfos](js-apis-inner-application-applicationContext.md#applicationcontextgetuiabilitychildprocessinfos).

**Since**: 26.0.1
 
**Model restriction:** This API can be used only in the stage model.
 
**System capability**: SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import
 
```ts
import { childProcessManager } from '@kit.AbilityKit';
```

## Properties
 
**Since**: 26.0.1
 
**Model restriction:** This API can be used only in the stage model.
 
**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| pid | number | No | No | PID of the child process. |
| parentPid | number | No | No | PID of the parent process of the child process. |
| processName | string | No | No | Name of the child process. |
