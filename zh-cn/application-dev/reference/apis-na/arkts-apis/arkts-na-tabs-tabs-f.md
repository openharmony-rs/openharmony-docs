# Tabs

## Tabs

```TypeScript
@ComponentBuilder
export declare function Tabs(
    options?: TabsOptions, 
    content_?: CustomBuilder,
): TabsAttribute
```

创建Tabs容器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Tabs(    options?: TabsOptions,     content_?: CustomBuilder,): TabsAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Tabs(    options?: TabsOptions,     content_?: CustomBuilder,): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TabsOptions | 否 | Tabs组件参数。 |
| content_ | CustomBuilder | 否 | 仅支持子组件TabContent，以及渲染控制类型 [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)，不建议自定义组件作为子组件。并且if/else和ForEach下也仅支持 TabContent作为子组件，不建议自定义组件作为子组件。<br/>**说明：** <br/>1. Tabs子组件设置了通用属性 [visibility](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-visibility.md#visibility)的值为None，或者设 置值为Hidden时，对应子组件不显示，但依然会在视窗内占位。<br/>2. 已经显示的Tabs子组件TabContent后续隐藏时不会被销毁，若需要页面懒加载和释放，可以参考 示例13。<br/>3. Tabs设置 [height](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#height)为auto时，可根据子组件高度自适应高度大小。设置 [width](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#width)为auto时，可根据子组件宽度自适应宽度大小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TabsAttribute |  |


## Tabs

```TypeScript
@Builder
export declare function Tabs(
 style_: CustomBuilderT<TabsAttribute>,
 content_?: CustomBuilder,
): TabsAttribute
```

定义Tabs组件

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Tabs( style_: CustomBuilderT<TabsAttribute>, content_?: CustomBuilder,): TabsAttribute--><!--Device-unnamed-@Builderexport declare function Tabs( style_: CustomBuilderT<TabsAttribute>, content_?: CustomBuilder,): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;TabsAttribute&gt; | 是 | tabs属性实例 |
| content_ | CustomBuilder | 否 | 内容区 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TabsAttribute |  |

