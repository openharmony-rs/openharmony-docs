# IndicatorComponent

## IndicatorComponent

```TypeScript
@ComponentBuilder
export declare function IndicatorComponent(
  controller?: IndicatorComponentController
): IndicatorComponentAttribute
```

单独导航点组件的构造函数，可配置该组件的控制器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function IndicatorComponent(  controller?: IndicatorComponentController): IndicatorComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function IndicatorComponent(  controller?: IndicatorComponentController): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [IndicatorComponentController](arkts-na-indicatorcomponent-indicatorcomponentcontroller-c.md) | 否 | IndicatorComponent constructor options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IndicatorComponentAttribute](arkts-na-indicatorcomponent-indicatorcomponentattribute-i.md) |  |


## IndicatorComponent

```TypeScript
@Builder
export declare function IndicatorComponent(
 style_: CustomBuilderT<IndicatorComponentAttribute>,
): IndicatorComponentAttribute
```

定义IndicatorComponent组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function IndicatorComponent( style_: CustomBuilderT<IndicatorComponentAttribute>,): IndicatorComponentAttribute--><!--Device-unnamed-@Builderexport declare function IndicatorComponent( style_: CustomBuilderT<IndicatorComponentAttribute>,): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[IndicatorComponentAttribute](arkts-na-indicatorcomponent-indicatorcomponentattribute-i.md)&gt; | 是 | indicatorComponent属性实例 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IndicatorComponentAttribute](arkts-na-indicatorcomponent-indicatorcomponentattribute-i.md) |  |

