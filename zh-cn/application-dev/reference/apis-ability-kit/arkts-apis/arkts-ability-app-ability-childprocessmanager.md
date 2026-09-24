# @ohos.app.ability.childProcessManager(子进程管理)

childProcessManager模块提供子进程管理能力，支持子进程创建和启动操作。创建的子进程会随着父进程的退出而退出，无法脱离父进程独立运行。

> **说明：** 
> 
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 本模块接口仅可在Stage模型下使用。

## 约束限制

### 功能限制

- 创建的子进程不支持创建UI界面。  
- 创建的子进程不支持依赖Context的API调用（包括Context模块自身API及将Context实例作为入参的API）。  
- 仅允许在主进程中创建子进程，子进程内不支持再次创建子进程。

### 规格限制

- 通过本模块中定义的创建子进程的接口和native_child_process.h中定义的创建子进程的接口启动的子进程总数最大为512个（系统资源充足情况下），  
其中startChildProcess接口在SELF_FORK模式下启动的子进程不计入总数内。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getChildProcessInfos](arkts-ability-childprocessmanager-getchildprocessinfos-f.md) | 获取当前应用的子进程信息。该接口使用promise返回的结果。返回的子进程包括通过创建的子进程[startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md) (在APP_SPAWN_FORK模式)，[startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md)，以及[startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md).【OH_Ability_CreateNativeChildProcess】【OH_Ability_CreateNativeChildProcessWithConfigs】【OH_Ability_StartNativeChildProcess】【OH_Ability_StartNativeChildProcessWithConfigs】 |
| [isArkChildProcessSupported](arkts-ability-childprocessmanager-isarkchildprocesssupported-f.md) | 查询是否允许调用者在此设备上创建ArkTS子进程 |
| [isNativeChildProcessSupported](arkts-ability-childprocessmanager-isnativechildprocesssupported-f.md) | 查询是否允许调用者在此设备上创建Native子进程 |
| [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。 |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startchildprocess) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。 |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startchildprocess-1) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用callback异步回调。 |
| [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md) | 启动[Native子进程](../../../application-models/ability-terminology.md#native子进程)。使用Promise异步回调。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ChildProcessInformation](arkts-ability-childprocessmanager-childprocessinformation-t.md) | 定义子进程信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | 子进程启动模式枚举。 |
