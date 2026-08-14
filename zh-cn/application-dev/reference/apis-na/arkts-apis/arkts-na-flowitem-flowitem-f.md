# FlowItem

## FlowItem

```TypeScript
@ComponentBuilder
export declare function FlowItem(
    content_?: CustomBuilder,
): FlowItemAttribute
```

创建瀑布流子组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function FlowItem(    content_?: CustomBuilder,): FlowItemAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function FlowItem(    content_?: CustomBuilder,): FlowItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 容器内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FlowItemAttribute |  |


## FlowItem

```TypeScript
@Builder
export declare function FlowItem(
    style_: CustomBuilderT<FlowItemAttribute>,
    content_?: CustomBuilder
): FlowItemAttribute
```

定义FlowItem组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function FlowItem(    style_: CustomBuilderT<FlowItemAttribute>,    content_?: CustomBuilder): FlowItemAttribute--><!--Device-unnamed-@Builderexport declare function FlowItem(    style_: CustomBuilderT<FlowItemAttribute>,    content_?: CustomBuilder): FlowItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;FlowItemAttribute&gt; | 是 | 用于创建FlowItem的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FlowItemAttribute | FlowItem的属性。 |

