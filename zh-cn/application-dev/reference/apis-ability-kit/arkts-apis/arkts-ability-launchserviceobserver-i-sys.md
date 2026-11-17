# LaunchServiceObserver（系统接口）

```TypeScript
declare interface LaunchServiceObserver
```

定义LaunchService状态和进程状态变化的观察者。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceObserver--><!--Device-unnamed-declare interface LaunchServiceObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onLaunchServiceProcessStateChanged

```TypeScript
onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void
```

在LaunchService进程状态改变时调用，包括进程启动和停止事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceObserver-onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void--><!--Device-LaunchServiceObserver-onLaunchServiceProcessStateChanged(processStateData: LaunchServiceProcessStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processStateData | [LaunchServiceProcessStateData](arkts-ability-launchserviceprocessstatedata-i-sys.md) | 是 | 进程状态变化数据。 |

## onLaunchServiceRegisteredChanged

```TypeScript
onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void
```

当LaunchService的注册状态发生变化（注册或解注册）时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceObserver-onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void--><!--Device-LaunchServiceObserver-onLaunchServiceRegisteredChanged(stateDataList: Array<LaunchServiceStateData>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stateDataList | Array&lt;[LaunchServiceStateData](arkts-ability-launchservicestatedata-i-sys.md)&gt; | 是 | 状态变化的LaunchService列表。 |
