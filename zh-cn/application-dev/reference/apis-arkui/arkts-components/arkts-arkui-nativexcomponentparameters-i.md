# NativeXComponentParameters

定义XComponent在Native侧使用的具体配置参数。通过这种构造参数创建的XComponent，可以将其对应的FrameNode对象传递至Native侧，使用NDK接口进行Surface生命周期的相关设置和添加事件监听。

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。未设置时不配置AI分析选项，仅类型为SURFACE或TEXTURE时有效。

**类型：** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

XComponent的类型。

**类型：** [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
