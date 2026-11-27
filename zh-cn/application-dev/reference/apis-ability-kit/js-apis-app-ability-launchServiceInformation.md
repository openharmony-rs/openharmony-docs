# LaunchServiceInformation

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

描述LaunchService的信息，包含服务描述符、注册及启用状态和进程pid。作为[getInformation](js-apis-app-ability-launchServiceManager.md#launchservicemanagergetinformation)接口的返回结果，以及getAllRegisteredInformation接口返回数组中的元素。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## LaunchServiceInformation

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 否 | 否 | LaunchService的描述符。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| state | [LaunchServiceState](js-apis-app-ability-launchServiceManager.md#launchservicestate) | 否 | 否 | LaunchService的状态。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| pid | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 否 | LaunchService进程的pid。0表示进程未启动，大于0时表示正在运行的进程的pid。<br>取值限定为正整数。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
