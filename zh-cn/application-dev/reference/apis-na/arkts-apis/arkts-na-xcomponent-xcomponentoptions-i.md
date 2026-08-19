# XComponentOptions

定义XComponent的具体配置参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface XComponentOptions--><!--Device-unnamed-export declare interface XComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: XComponentController
```

给组件绑定一个控制器，通过控制器调用组件方法，仅类型为SURFACE或TEXTURE时有效。 未设置时不绑定控制器。

**类型：** [XComponentController](arkts-na-xcomponent-xcomponentcontroller-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentOptions-controller: XComponentController--><!--Device-XComponentOptions-controller: XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器， 仅类型为SURFACE或TEXTURE时有效。未设置时不配置AI分析选项， 可通过enableAnalyzer属性单独启用AI分析。

**类型：** [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions--><!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

用于指定XComponent组件类型。

**类型：** [XComponentType](../../apis-arkui/arkts-apis/arkts-arkui-xcomponenttype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentOptions-type: XComponentType--><!--Device-XComponentOptions-type: XComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

