# FullScreenLaunchComponent

全屏启动原子化服务组件，当被拉起方授权使用方可以嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 > **说明：** > > 如果需要在该组件中实现可嵌入式运行的原子化服务，必须继承自[EmbeddableUIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 。否则，系统无法保证原子化服务功能正常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct FullScreenLaunchComponent--><!--Device-unnamed-export declare struct FullScreenLaunchComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

The method to build component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

<!--Device-FullScreenLaunchComponent-build(): void--><!--Device-FullScreenLaunchComponent-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appId

```TypeScript
appId: string
```

Indicates atomic service appId.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FullScreenLaunchComponent-appId: string--><!--Device-FullScreenLaunchComponent-appId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ContentBuilder
```

Sets the component content.

**类型：** ContentBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @BuilderParam

<!--Device-FullScreenLaunchComponent-content: ContentBuilder--><!--Device-FullScreenLaunchComponent-content: ContentBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onError

```TypeScript
onError?: ErrorCallback
```

Callback triggered when an error occurs during running of the started ExtensionAbility. It is supported only when the atomic service runs in embedded mode, with the parameter being of type BusinessError.

**类型：** ErrorCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FullScreenLaunchComponent-onError?: ErrorCallback--><!--Device-FullScreenLaunchComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onReceive

```TypeScript
onReceive?: Callback<Record<string, RecordData>>
```

Indicates the callback of onReceive.

**类型：** Callback&lt;Record&lt;string, RecordData&gt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FullScreenLaunchComponent-onReceive?: Callback<Record<string, RecordData>>--><!--Device-FullScreenLaunchComponent-onReceive?: Callback<Record<string, RecordData>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

Callback triggered when the EmbeddableUIAbility is terminated to receive the information about the termination. It is supported only when the atomic service runs in embedded mode, with the parameter being of type TerminationInfo.

**类型：** Callback&lt;TerminationInfo&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>--><!--Device-FullScreenLaunchComponent-onTerminated?: Callback<TerminationInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: AtomicServiceOptions
```

Indicates the atomic service start options.

**类型：** AtomicServiceOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FullScreenLaunchComponent-options?: AtomicServiceOptions--><!--Device-FullScreenLaunchComponent-options?: AtomicServiceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

