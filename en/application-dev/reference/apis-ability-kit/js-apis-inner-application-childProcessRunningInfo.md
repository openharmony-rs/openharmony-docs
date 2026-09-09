# ChildProcessInformation
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f0ca4679538114d37c428618ebeb98dcc5067c5b translatedAt=2026-09-03T11:53:24.321Z pushedAt=2026-09-05T10:47:30.712Z -->

ChildProcessInformation defines the information about a child process, including the PID of the child process, the PID of the parent process, and the name of the child process. It can be obtained through [getChildProcessInfos](js-apis-app-ability-childProcessManager.md#childprocessmanagergetchildprocessinfos) and [getUIAbilityChildProcessInfos](js-apis-inner-application-applicationContext.md#applicationcontextgetuiabilitychildprocessinfos).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

## Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| pid | int | No | No | PID of the child process. |
| parentPid | int | No | No | PID of the parent process of the child process. |
| processName | string | No | No | Name of the child process. |
