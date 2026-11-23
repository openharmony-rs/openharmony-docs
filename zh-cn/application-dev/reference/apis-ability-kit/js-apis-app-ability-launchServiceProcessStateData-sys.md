# LaunchServiceProcessStateData (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

描述LaunchService进程状态变化数据，包含服务描述符、进程pid和进程状态。作为[onLaunchServiceProcessStateChanged](js-apis-app-ability-launchServiceObserver-sys.md#onlaunchserviceprocessstatechanged)回调的processStateData参数，在服务进程启动或停止时传递。

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

## LaunchServiceProcessStateData

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 否 | 否 | 启动服务的描述符。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| pid | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 否 | LaunchService进程的pid。0表示进程未在运行，大于0表示正在运行进程的pid。<br>取值限定为正整数。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| state | [LaunchServiceProcessState](js-apis-app-ability-launchServiceManager-sys.md#launchserviceprocessstate) | 否 | 否 | LaunchService进程状态。<br>0：LaunchService进程启动。<br>1：LaunchService进程停止。<br>取值限定为0或1。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
