# NativeXComponentParameters

定义XComponent的具体配置参数。通过这种构造参数创建的XComponent，可以将其对应的FrameNode对象传递至Native侧， 使用NDK接口进行Surface生命周期的相关设置和添加事件监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NativeXComponentParameters--><!--Device-unnamed-export declare interface NativeXComponentParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 未设置时不配置AI分析选项，仅类型为SURFACE或TEXTURE时有效。

**类型：** ImageAIOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions--><!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

用于指定XComponent组件类型。

**类型：** XComponentType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NativeXComponentParameters-type: XComponentType--><!--Device-NativeXComponentParameters-type: XComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

