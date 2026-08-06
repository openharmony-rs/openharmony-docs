# Column

## Column

```TypeScript
export declare function Column(
    options?: ColumnOptions | ColumnOptions | ColumnOptionsV2,
    content_?: CustomBuilder,
): ColumnAttribute
```

沿垂直方向布局的容器。 > **说明：** > > Column未设置高度或宽度时，在主轴或交叉轴方向上自适应子组件大小。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Column(    options?: ColumnOptions | ColumnOptions | ColumnOptionsV2,    content_?: CustomBuilder,): ColumnAttribute--><!--Device-unnamed-export declare function Column(    options?: ColumnOptions | ColumnOptions | ColumnOptionsV2,    content_?: CustomBuilder,): ColumnAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ColumnOptions \| ColumnOptionsV2 | 否 | Column options. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## Column

```TypeScript
export declare function Column(
    style: CustomBuilderT<ColumnAttribute>,
    content_?: CustomBuilder,
): ColumnAttribute
```

Defines Column Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Column(    style: CustomBuilderT<ColumnAttribute>,    content_?: CustomBuilder,): ColumnAttribute--><!--Device-unnamed-export declare function Column(    style: CustomBuilderT<ColumnAttribute>,    content_?: CustomBuilder,): ColumnAttribute-End-->

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

