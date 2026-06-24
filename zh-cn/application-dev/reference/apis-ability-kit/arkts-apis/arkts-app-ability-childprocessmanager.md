# @ohos.app.ability.childProcessManager

childProcessManager模块提供子进程管理能力，支持子进程创建和启动操作。
创建的子进程会随着父进程的退出而退出，无法脱离父进程独立运行。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md#startArkChildProcess-1) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。<br/>该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 调用该接口创建的子进程不会继承父进程资源，子进程创建成功会返回子进程pid，然后执行子进程的<br/>&gt; [ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数。<br/>&gt; [ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数执行完后子进程不会自动销毁，需要子进程调用<br/>&gt; [process.abort](../../apis-arkts/arkts-apis/arkts-arkts-process-abort-f.md#abort-1)销毁。调用该接口的进程销毁后，所创建的子进程也会一并销毁。<br/> |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startChildProcess-1) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。<br/>该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 调用该接口创建子进程成功会返回子进程pid，然后执行子进程的[ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数<br/>&gt; ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数执行完后子进程会自动销毁。<br/>&gt;<br/>&gt; 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。<br/> |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startChildProcess-2) | 启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用callback异步回调。<br/>该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 调用该接口创建子进程成功会返回子进程pid，然后执行子进程的[ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数<br/>&gt; ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onStart-1)函数执行完后子进程会自动销毁。<br/>&gt;<br/>&gt; 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。<br/> |
| [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md#startNativeChildProcess-1) | 启动[Native子进程](../../../../application-models/ability-terminology.md#native子进程)。使用Promise异步回调。<br/>该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 调用该接口创建的子进程不会继承父进程资源，子进程创建成功会返回子进程pid，然后加载参数中指定的动态链接库文件并执行子进程的入口函数，入口函数执行完后子进程会自动销毁。调用该接口的进程销毁后，所创建的子进程也会一并销毁。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | 子进程启动模式枚举。<br/> |

