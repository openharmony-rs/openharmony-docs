# HalfScreenLaunchComponent

半屏嵌入式启动原子化服务组件，当被拉起方未授权嵌入式运行原子化服务时，宿主将使用跳出式拉起原子化服务。 > **说明：** > > 如果需要在该组件中实现一个可嵌入式运行的原子化服务时，原子化服务必须继承自 > [EmbeddableUIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。若不继承自EmbeddableUIAbility，系统无 > 法确保原子化服务正常运行。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct HalfScreenLaunchComponent--><!--Device-unnamed-export declare struct HalfScreenLaunchComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appId

```TypeScript
appId: string
```

原子化服务appId。

**类型：** string

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-appId: string--><!--Device-HalfScreenLaunchComponent-appId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: Callback<void>
```

组件显示内容。

**类型：** Callback&lt;void&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @BuilderParam

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-content: Callback<void>--><!--Device-HalfScreenLaunchComponent-content: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onError

```TypeScript
onError?: ErrorCallback
```

被拉起的原子化服务扩展在运行过程中发生异常时触发本回调。

**类型：** ErrorCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onError?: ErrorCallback--><!--Device-HalfScreenLaunchComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

被拉起的嵌入式运行原子化服务通过[@ohos.window (窗口)]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_调用API时，触发本回调。

**类型：** Callback&lt;Record&lt;string, Object&gt;&gt;

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>--><!--Device-HalfScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

被拉起的嵌入式运行原子化服务通过点击原子化服务退出按钮、手势侧滑、调用 [terminateSelfWithResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或者 [terminateSelf]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 正常退出时，触发本回调函数。

**类型：** Callback&lt;TerminationInfo&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>--><!--Device-HalfScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: AtomicServiceOptions
```

拉起原子化服务参数，默认为空。

**类型：** AtomicServiceOptions

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-options?: AtomicServiceOptions--><!--Device-HalfScreenLaunchComponent-options?: AtomicServiceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

