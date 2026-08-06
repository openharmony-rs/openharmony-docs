# XComponentOptions

定义XComponent的选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface XComponentOptions--><!--Device-unnamed-declare interface XComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: XComponentController
```

绑定到组件的控制器，可用于调用组件的方法。 该参数仅在type为SURFACE或TEXTURE时有效。

**类型：** XComponentController

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentOptions-controller: XComponentController--><!--Device-XComponentOptions-controller: XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器，仅类型为SURFACE或TEXTURE时有效。未设置时不配置AI分析选项，可通过[enableAnalyzer]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性单独启用AI分析。

**类型：** ImageAIOptions

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions--><!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

组件的类型。

**类型：** XComponentType

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentOptions-type: XComponentType--><!--Device-XComponentOptions-type: XComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

