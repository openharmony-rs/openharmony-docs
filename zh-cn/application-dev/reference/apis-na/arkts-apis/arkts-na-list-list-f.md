# List

## List

```TypeScript
@ComponentBuilder
export declare function List(
    options?: ListOptions, 
    content_?: CustomBuilder,
): ListAttribute
```

定义List组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function List(    options?: ListOptions,     content_?: CustomBuilder,): ListAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function List(    options?: ListOptions,     content_?: CustomBuilder,): ListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-na-list-listoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListAttribute |  |


## List

```TypeScript
@Builder
export declare function List(
    style_: CustomBuilderT<ListAttribute>,
    content_?: CustomBuilder
): ListAttribute
```

可扩展List组件的入口。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function List(    style_: CustomBuilderT<ListAttribute>,    content_?: CustomBuilder): ListAttribute--><!--Device-unnamed-@Builderexport declare function List(    style_: CustomBuilderT<ListAttribute>,    content_?: CustomBuilder): ListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ListAttribute&gt; | 是 | The style to create a List. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListAttribute | The attribute of the List. |

