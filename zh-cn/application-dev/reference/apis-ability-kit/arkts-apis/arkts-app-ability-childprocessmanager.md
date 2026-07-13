# @ohos.app.ability.childProcessManager

childProcessManager模块提供子进程管理能力，支持子进程创建和启动操作。
创建的子进程会随着父进程的退出而退出，无法脱离父进程独立运行。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [startArkChildProcess](arkts-ability-startarkchildprocess-f.md#startarkchildprocess-1) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。@link @ohos.app.ability.ChildProcess:ChildProcess#onStart}函数。&gt; [ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数执行完后子进程不会自动销毁，需要子进程调用&gt; [process.abort](../../apis-arkts/arkts-apis/arkts-arkts-abort-f.md#abort-1)销毁。调用该接口的进程销毁后，所创建的子进程也会一并销毁。 |
| [startChildProcess](arkts-ability-startchildprocess-f.md#startchildprocess-1) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。@link @ohos.app.ability.ChildProcess:ChildProcess#onStart}函数&gt; ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数执行完后子进程会自动销毁。&gt;&gt; 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。 |
| [startChildProcess](arkts-ability-startchildprocess-f.md#startchildprocess-2) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用callback异步回调。该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。@link @ohos.app.ability.ChildProcess:ChildProcess#onStart}函数&gt; ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数执行完后子进程会自动销毁。&gt;&gt; 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。 |
| [startNativeChildProcess](arkts-ability-startnativechildprocess-f.md#startnativechildprocess-1) | 启动[Native子进程](../../../../application-models/ability-terminology.md#native子进程)。使用Promise异步回调。该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StartMode](arkts-ability-startmode-e.md) | 子进程启动模式枚举。 |

