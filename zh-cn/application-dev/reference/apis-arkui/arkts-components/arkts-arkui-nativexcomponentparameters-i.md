# NativeXComponentParameters

定义native xcomponent参数。使用此类构造参数创建的XComponent可以将其对应的FrameNode对象传递到Native侧，从而能够使用NDK接口进行surface生命周期相关设置和[组件事件监听](../../../ui/ndk-listen-to-component-events.md)。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

<!--Device-unnamed-declare interface NativeXComponentParameters--><!--Device-unnamed-declare interface NativeXComponentParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。未设置时不配置AI分析选项，仅类型为SURFACE或TEXTURE时有效。

**类型：** ImageAIOptions

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions--><!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

XComponent的类型。

**类型：** [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md)

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NativeXComponentParameters-type: XComponentType--><!--Device-NativeXComponentParameters-type: XComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

