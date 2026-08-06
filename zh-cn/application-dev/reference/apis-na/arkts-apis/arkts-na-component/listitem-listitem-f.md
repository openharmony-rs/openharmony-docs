# ListItem

## ListItem

```TypeScript
export declare function ListItem(
    value?: ListItemOptions, 
    content_?: CustomBuilder,
): ListItemAttribute
```

创建ListItem组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ListItem(    value?: ListItemOptions,     content_?: CustomBuilder,): ListItemAttribute--><!--Device-unnamed-export declare function ListItem(    value?: ListItemOptions,     content_?: CustomBuilder,): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## ListItem

```TypeScript
export declare function ListItem(
    style_: CustomBuilderT<ListItemAttribute>,
    content_?: CustomBuilder
): ListItemAttribute
```

可扩展的ListItem组件的入口。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ListItem(    style_: CustomBuilderT<ListItemAttribute>,    content_?: CustomBuilder): ListItemAttribute--><!--Device-unnamed-export declare function ListItem(    style_: CustomBuilderT<ListItemAttribute>,    content_?: CustomBuilder): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | The style to create a ListItem. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The attribute of the ListItem. |

