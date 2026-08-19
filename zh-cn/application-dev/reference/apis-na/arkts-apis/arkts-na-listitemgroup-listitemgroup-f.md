# ListItemGroup

## ListItemGroup

```TypeScript
@ComponentBuilder
export declare function ListItemGroup(
    options?: ListItemGroupOptions, 
    content_?: CustomBuilder,
): ListItemGroupAttribute
```

创建ListItemGroup组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ListItemGroup(    options?: ListItemGroupOptions,     content_?: CustomBuilder,): ListItemGroupAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ListItemGroup(    options?: ListItemGroupOptions,     content_?: CustomBuilder,): ListItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListItemGroupOptions](arkts-na-listitemgroup-listitemgroupoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 | 容器内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListItemGroupAttribute |  |


## ListItemGroup

```TypeScript
@Builder
export declare function ListItemGroup(
    style_: CustomBuilderT<ListItemGroupAttribute>,
    content_?: CustomBuilder
): ListItemGroupAttribute
```

定义ListItemGroup组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ListItemGroup(    style_: CustomBuilderT<ListItemGroupAttribute>,    content_?: CustomBuilder): ListItemGroupAttribute--><!--Device-unnamed-@Builderexport declare function ListItemGroup(    style_: CustomBuilderT<ListItemGroupAttribute>,    content_?: CustomBuilder): ListItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ListItemGroupAttribute&gt; | 是 | 创建ListItemGroup的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListItemGroupAttribute | ListItemGroup的属性。 |

