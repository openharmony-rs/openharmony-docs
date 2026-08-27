# XComponentOptions

定义XComponent的选项。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## controller

```TypeScript
controller: XComponentController
```

绑定到组件的控制器，可用于调用组件的方法。 该参数仅在type为SURFACE或TEXTURE时有效。

**类型：** [XComponentController](arkts-arkui-xcomponentcontroller-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器，仅类型为SURFACE或TEXTURE时有效。未设置时不配置AI分析选项，可通过[enableAnalyzer](arkts-arkui-xcomponent-attribute.md#enableanalyzer)属性单独启用AI分析。

**类型：** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

组件的类型。

**类型：** [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
