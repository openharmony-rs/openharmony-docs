# GridCol

## GridCol

```TypeScript
@ComponentBuilder
export declare function GridCol(
    option?: GridColOptions, 
    content_?: CustomBuilder,
): GridColAttribute
```

栅格列布局组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function GridCol(    option?: GridColOptions,     content_?: CustomBuilder,): GridColAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function GridCol(    option?: GridColOptions,     content_?: CustomBuilder,): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridColOptions](arkts-arkui-gridcol-gridcoloptions-i.md) | 否 | 栅格布局子组件参数。 |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GridColAttribute |  |


## GridCol

```TypeScript
@Builder
export declare function GridCol(
    style: CustomBuilderT<GridColAttribute>,
    content_?: CustomBuilder,
): GridColAttribute
```

Defines GridCol Component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function GridCol(    style: CustomBuilderT<GridColAttribute>,    content_?: CustomBuilder,): GridColAttribute--><!--Device-unnamed-@Builderexport declare function GridCol(    style: CustomBuilderT<GridColAttribute>,    content_?: CustomBuilder,): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;GridColAttribute&gt; | 是 | the callback to set up component's attributes. |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GridColAttribute |  |

