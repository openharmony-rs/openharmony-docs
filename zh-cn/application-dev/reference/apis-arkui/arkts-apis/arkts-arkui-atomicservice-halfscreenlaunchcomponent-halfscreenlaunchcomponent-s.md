# HalfScreenLaunchComponent

半屏嵌入式启动原子化服务组件，当被拉起方未授权嵌入式运行原子化服务时，宿主将使用跳出式拉起原子化服务。 > **说明：** > > 该组件从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 当需要在该组件中实现一个可嵌入式运行的原子化服务时，原子化服务必须继承自 > [EmbeddableUIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md#EmbeddableUIAbility)。若不继承自EmbeddableUIAbility，系统无 > 法确保原子化服务正常运行。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

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

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-appId: string--><!--Device-HalfScreenLaunchComponent-appId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@BuilderParam
  content: Callback<void>
```

组件显示内容。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-@BuilderParam  content: Callback<void>--><!--Device-HalfScreenLaunchComponent-@BuilderParam  content: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onError

```TypeScript
onError?: ErrorCallback
```

被拉起的原子化服务在运行过程中发生异常时触发本回调。

**类型：** [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onError?: ErrorCallback--><!--Device-HalfScreenLaunchComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

被拉起的嵌入式运行原子化服务通过[@ohos.window (窗口)](arkts-arkui-window-n.md#window)调用相关API时，触发本回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt;

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>--><!--Device-HalfScreenLaunchComponent-onReceive?: Callback<Record<string, Object>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

被拉起的嵌入式运行原子化服务通过点击原子化服务退出按钮、手势侧滑、调用 terminateSelfWithResult 或者 [terminateSelf](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#terminateSelf) 正常退出时，触发本回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;TerminationInfo&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>--><!--Device-HalfScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: AtomicServiceOptions
```

拉起原子化服务参数。不填时使用默认参数拉起原子化服务。

**类型：** [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HalfScreenLaunchComponent-options?: AtomicServiceOptions--><!--Device-HalfScreenLaunchComponent-options?: AtomicServiceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

