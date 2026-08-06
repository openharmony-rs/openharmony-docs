# ColumnSplit

## ColumnSplit

```TypeScript
export declare function ColumnSplit(
    
    content_?: CustomBuilder,
): ColumnSplitAttribute
```

将子组件纵向布局，并在每个子组件之间插入横向分割线。 ColumnSplit通过分割线限制子组件的高度。初始化时，分割线位置根据子组件的高度来计算。 初始化后，动态修改子组件的高度不生效，分割线位置保持不变，可通过拖动相邻分割线改变子组件高度。 初始化后，动态修改 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 通用属性导致子组件尺寸大于相邻分割线间距的异常情况下，不支持拖动分割线改变子组件的高度。 > **说明：** > > ColumnSplit组件 > \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_ > 的默认值为true。 > > 与\_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_相同， > ColumnSplit的分割线可调整上下两侧子组件的高度， > 子组件的高度调整范围受其最大最小高度限制。 > > 支持\_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_、 > \_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_ > 等通用属性，未设置clip属性时，其默认值为true。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ColumnSplit(        content_?: CustomBuilder,): ColumnSplitAttribute--><!--Device-unnamed-export declare function ColumnSplit(        content_?: CustomBuilder,): ColumnSplitAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 定义子组件的Builder函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## ColumnSplit

```TypeScript
export declare function ColumnSplit(
    style: CustomBuilderT<ColumnSplitAttribute>,
    content_?: CustomBuilder,
): ColumnSplitAttribute
```

Defines ColumnSplit Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ColumnSplit(    style: CustomBuilderT<ColumnSplitAttribute>,    content_?: CustomBuilder,): ColumnSplitAttribute--><!--Device-unnamed-export declare function ColumnSplit(    style: CustomBuilderT<ColumnSplitAttribute>,    content_?: CustomBuilder,): ColumnSplitAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | the callback to set up component's attributes. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

