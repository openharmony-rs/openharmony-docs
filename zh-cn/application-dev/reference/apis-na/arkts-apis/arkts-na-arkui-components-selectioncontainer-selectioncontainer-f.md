# SelectionContainer

## 导入模块

```TypeScript
```

## SelectionContainer

```TypeScript
@ComponentBuilder
export declare function SelectionContainer(content_?: CustomBuilder): SelectionContainerAttribute
```

创建一个SelectionContainer组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function SelectionContainer(content_?: CustomBuilder): SelectionContainerAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function SelectionContainer(content_?: CustomBuilder): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) |  |


## SelectionContainer

```TypeScript
@Builder
export declare function SelectionContainer(
    style: CustomBuilderT<SelectionContainerAttribute>
): SelectionContainerAttribute
```

创建一个SelectionContainer组件。需要在组件属性设置开始时调用setSelectionContainerOptions，并在组件属性设置结束时调用applyAttributesFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function SelectionContainer(    style: CustomBuilderT<SelectionContainerAttribute>): SelectionContainerAttribute--><!--Device-unnamed-@Builderexport declare function SelectionContainer(    style: CustomBuilderT<SelectionContainerAttribute>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[SelectionContainerAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md)&gt; | 是 | 设置SelectionContainer属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

