# ChildProcessInformation
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

ChildProcessInformation定义子进程信息，包括子进程的PID、父进程PID及子进程名称等，可以通过[getChildProcessInfos](js-apis-app-ability-childProcessManager.md#childprocessmanagergetchildprocessinfos)、[getUIAbilityChildProcessInfos](js-apis-inner-application-applicationContext.md#applicationcontextgetuiabilitychildprocessinfos)方法获取。

**起始版本**：26.1.0
 
**模型约束**：此接口仅可在Stage模型下使用。
 
**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| pid | int | 否 | 否 | 子进程的PID。 |
| parentPid | int | 否 | 否 | 子进程的父进程PID。 |
| processName | string | 否 | 否 | 子进程的进程名。 |
