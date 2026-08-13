# @ohos.app.ability.childProcessManager

childProcessManager模块提供子进程管理能力，支持子进程创建和启动操作。 创建的子进程会随着父进程的退出而退出，无法脱离父进程独立运行。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace childProcessManager--><!--Device-unnamed-declare namespace childProcessManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md#startArkChildProcess) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。 该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startChildProcess) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。 该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。 |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startChildProcess) | 启动[ArkTS子进程](../../../application-models/ability-terminology.md#arkts子进程)。使用callback异步回调。 该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。 |
| [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md#startNativeChildProcess) | 启动[Native子进程](../../../application-models/ability-terminology.md#native子进程)。使用Promise异步回调。 该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | 子进程启动模式枚举。 |

