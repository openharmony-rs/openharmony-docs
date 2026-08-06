# InnerFullScreenLaunchComponent（系统接口）

非显式全屏启动原子化服务组件，拉起方可以选择拉起原子化服务的时机。当被拉起方授权使用方可以嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 > **说明：** > > 如果需要在该组件中实现一个可嵌入式运行的原子化服务时，必须继承自 > [EmbeddableUIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。若不继承自EmbeddableUIAbility，系统无 > 法保证原子化服务功能正常。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct InnerFullScreenLaunchComponent--><!--Device-unnamed-export declare struct InnerFullScreenLaunchComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content: Callback<void>
```

组件显示内容。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @BuilderParam

<!--Device-InnerFullScreenLaunchComponent-content: Callback<void>--><!--Device-InnerFullScreenLaunchComponent-content: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## controller

```TypeScript
controller: LaunchController
```

拉起原子化服务控制器。

**类型：** LaunchController

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-InnerFullScreenLaunchComponent-controller: LaunchController--><!--Device-InnerFullScreenLaunchComponent-controller: LaunchController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onError

```TypeScript
onError?: ErrorCallback
```

被拉起的嵌入式运行原子化服务在运行过程中发生异常时触发本回调。可通过回调参数中的code、name和message获取错误信息并做处理。

**类型：** ErrorCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-InnerFullScreenLaunchComponent-onError?: ErrorCallback--><!--Device-InnerFullScreenLaunchComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

被拉起的嵌入式运行原子化服务通过[@ohos.window (窗口)]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_调用API时，触发本回调。

**类型：** Callback&lt;Record&lt;string, Object&gt;&gt;

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-InnerFullScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>--><!--Device-InnerFullScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

被拉起的嵌入式运行原子化服务通过点击原子化服务退出按钮、手势侧滑、调用 [terminateSelfWithResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或者 [terminateSelf]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 正常退出时，触发本回调函数。

**类型：** Callback&lt;TerminationInfo&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-InnerFullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>--><!--Device-InnerFullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

