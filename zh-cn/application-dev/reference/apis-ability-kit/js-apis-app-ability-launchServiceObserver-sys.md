# LaunchServiceObserver (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义LaunchService状态和进程状态变化的观察者。作为[onLaunchServiceObserver](js-apis-app-ability-launchServiceManager-sys.md#launchservicemanageronlaunchserviceobserver)接口的observer参数，用于接收服务注册、注销及进程启动、停止的通知。通过[offLaunchServiceObserver](js-apis-app-ability-launchServiceManager-sys.md#launchservicemanagerofflaunchserviceobserver)接口传入注册时返回的观察者ID，可注销监听。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## onLaunchServiceRegisteredChanged

onLaunchServiceRegisteredChanged(stateDataList: Array&lt;LaunchServiceStateData&gt;): void

当LaunchService的注册状态发生变化（注册或解注册）时调用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| stateDataList |  Array&lt;[LaunchServiceStateData](js-apis-app-ability-launchServiceStateData-sys.md)&gt;  | 是 | 状态变化的LaunchService列表。 |

## onLaunchServiceProcessStateChanged

onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void

在LaunchService进程状态改变时调用，包括进程启动和停止事件。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| processStateData |  [LaunchServiceProcessStateData](js-apis-app-ability-launchServiceProcessStateData-sys.md)  | 是 | 进程状态变化数据。 |

