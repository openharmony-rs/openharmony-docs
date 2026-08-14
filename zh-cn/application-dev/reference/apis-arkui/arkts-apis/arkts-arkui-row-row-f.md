# Row

## Row

```TypeScript
@ComponentBuilder
export declare function Row(
    options?: RowOptions | RowOptions | RowOptionsV2,
    content_?: CustomBuilder,
): RowAttribute
```

创建水平方向线性布局容器，可以设置子组件的间距。 > 说明： > > 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。 > 建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。 > 最佳实践请参考[布局优化指导](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve-layout-performance)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Row(    options?: RowOptions | RowOptions | RowOptionsV2,    content_?: CustomBuilder,): RowAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Row(    options?: RowOptions | RowOptions | RowOptionsV2,    content_?: CustomBuilder,): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-row-rowoptions-i.md) \| [RowOptions](arkts-arkui-row-rowoptions-i.md) \| [RowOptionsV2](arkts-arkui-row-rowoptionsv2-i.md) | 否 | 横向布局元素间距，支持设置number、string或Resource类型。 |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RowAttribute |  |


## Row

```TypeScript
@Builder
export declare function Row(
    style: CustomBuilderT<RowAttribute>,
    content_?: CustomBuilder,
): RowAttribute
```

Defines Row Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Row(    style: CustomBuilderT<RowAttribute>,    content_?: CustomBuilder,): RowAttribute--><!--Device-unnamed-@Builderexport declare function Row(    style: CustomBuilderT<RowAttribute>,    content_?: CustomBuilder,): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;RowAttribute&gt; | 是 | the callback to set up component's attributes. |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RowAttribute |  |

