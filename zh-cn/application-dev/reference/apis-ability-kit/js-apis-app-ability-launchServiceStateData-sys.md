# LaunchServiceStateData (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

描述LaunchService注册状态变化数据，包含服务描述符和变化后的注册状态。作为[onLaunchServiceRegisteredChanged](js-apis-app-ability-launchServiceObserver-sys.md#onlaunchserviceregisteredchanged)回调的stateDataList数组中的元素，在服务注册或注销时传递。

**起始版本**：26.1.0

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## LaunchServiceStateData

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 否 | 否 | LaunchService的描述符。 |
| registered | boolean | 否 | 否 | LaunchService注册状态发生变化后的最新状态。true表示已注册，false表示未注册。 |
