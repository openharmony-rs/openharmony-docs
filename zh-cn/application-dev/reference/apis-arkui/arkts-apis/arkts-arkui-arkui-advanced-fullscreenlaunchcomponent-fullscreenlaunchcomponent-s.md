# FullScreenLaunchComponent

全屏启动原子化服务组件，当提供方授权使用方嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 > **说明：** > > 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 当需要在该组件中实现可嵌入式运行的原子化服务，必须继承自[EmbeddableUIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md#EmbeddableUIAbility)。 > 否则，系统无法保证原子化服务功能正常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare struct FullScreenLaunchComponent--><!--Device-unnamed-export declare struct FullScreenLaunchComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
@Builder
  build(): void
```

构建组件的方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-@Builder  build(): void--><!--Device-FullScreenLaunchComponent-@Builder  build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appId

```TypeScript
appId: string
```

表示原子化服务appId。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-appId: string--><!--Device-FullScreenLaunchComponent-appId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@BuilderParam
  content: ContentBuilder
```

设置组件内容。

**类型：** [ContentBuilder](arkts-arkui-contentbuilder-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-@BuilderParam  content: ContentBuilder--><!--Device-FullScreenLaunchComponent-@BuilderParam  content: ContentBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onError

```TypeScript
onError?: ErrorCallback
```

在启动的ExtensionAbility运行过程中发生错误时触发回调。仅在原子服务以嵌入式模式运行时支持，参数类型为BusinessError。

**类型：** [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-onError?: ErrorCallback--><!--Device-FullScreenLaunchComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onReceive

```TypeScript
onReceive?: Callback<Record<string, RecordData>>
```

表示onReceive的回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-onReceive?: Callback<Record<string, RecordData>>--><!--Device-FullScreenLaunchComponent-onReceive?: Callback<Record<string, RecordData>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

当EmbeddableUIAbility被终止时触发回调，用于接收终止信息。仅在原子化服务以嵌入式模式运行时支持该回调，参数类型为TerminationInfo。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;TerminationInfo&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>--><!--Device-FullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: AtomicServiceOptions
```

表示原子化服务启动选项。

**类型：** [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-FullScreenLaunchComponent-options?: AtomicServiceOptions--><!--Device-FullScreenLaunchComponent-options?: AtomicServiceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

