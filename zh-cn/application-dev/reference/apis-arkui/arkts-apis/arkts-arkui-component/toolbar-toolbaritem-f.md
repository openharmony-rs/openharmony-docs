# ToolBarItem

## ToolBarItem

```TypeScript
export declare function ToolBarItem(
    options?: ToolBarItemOptions,
    content_?: CustomBuilder,
): ToolBarItemAttribute
```

定义ToolBarItem组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ToolBarItem(    options?: ToolBarItemOptions,    content_?: CustomBuilder,): ToolBarItemAttribute--><!--Device-unnamed-export declare function ToolBarItem(    options?: ToolBarItemOptions,    content_?: CustomBuilder,): ToolBarItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 分栏选项 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 容器 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## ToolBarItem

```TypeScript
export declare function ToolBarItem(
    style: CustomBuilderT<ToolBarItemAttribute>,
    content_?: CustomBuilder,
): ToolBarItemAttribute
```

定义ToolBarItem组件。需要在组件属性设置开始时调用setToolBarItemOptions， 并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ToolBarItem(    style: CustomBuilderT<ToolBarItemAttribute>,    content_?: CustomBuilder,): ToolBarItemAttribute--><!--Device-unnamed-export declare function ToolBarItem(    style: CustomBuilderT<ToolBarItemAttribute>,    content_?: CustomBuilder,): ToolBarItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置toolbaritem属性的回调。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | ToolBarItem的属性。 |

