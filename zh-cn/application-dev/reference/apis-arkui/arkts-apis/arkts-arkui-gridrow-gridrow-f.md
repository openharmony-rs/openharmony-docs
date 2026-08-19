# GridRow

## GridRow

```TypeScript
@ComponentBuilder
export declare function GridRow(
    option?: GridRowOptions, 
    content_?: CustomBuilder,
): GridRowAttribute
```

栅格行布局容器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function GridRow(    option?: GridRowOptions,     content_?: CustomBuilder,): GridRowAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function GridRow(    option?: GridRowOptions,     content_?: CustomBuilder,): GridRowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridRowOptions](arkts-arkui-gridrow-gridrowoptions-i.md) | 否 | 栅格布局子组件参数。 |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GridRowAttribute |  |


## GridRow

```TypeScript
@Builder
export declare function GridRow(
    style: CustomBuilderT<GridRowAttribute>,
    content_?: CustomBuilder,
): GridRowAttribute
```

Defines GridRow Component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function GridRow(    style: CustomBuilderT<GridRowAttribute>,    content_?: CustomBuilder,): GridRowAttribute--><!--Device-unnamed-@Builderexport declare function GridRow(    style: CustomBuilderT<GridRowAttribute>,    content_?: CustomBuilder,): GridRowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;GridRowAttribute&gt; | 是 | the callback to set up component's attributes. |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GridRowAttribute |  |

