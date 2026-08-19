# ListItem

## ListItem

```TypeScript
@ComponentBuilder
export declare function ListItem(
    value?: ListItemOptions, 
    content_?: CustomBuilder,
): ListItemAttribute
```

创建ListItem组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ListItem(    value?: ListItemOptions,     content_?: CustomBuilder,): ListItemAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ListItem(    value?: ListItemOptions,     content_?: CustomBuilder,): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListItemOptions](arkts-na-listitem-listitemoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListItemAttribute |  |


## ListItem

```TypeScript
@Builder
export declare function ListItem(
    style_: CustomBuilderT<ListItemAttribute>,
    content_?: CustomBuilder
): ListItemAttribute
```

可扩展的ListItem组件的入口。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ListItem(    style_: CustomBuilderT<ListItemAttribute>,    content_?: CustomBuilder): ListItemAttribute--><!--Device-unnamed-@Builderexport declare function ListItem(    style_: CustomBuilderT<ListItemAttribute>,    content_?: CustomBuilder): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ListItemAttribute&gt; | 是 | The style to create a ListItem. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListItemAttribute | The attribute of the ListItem. |

