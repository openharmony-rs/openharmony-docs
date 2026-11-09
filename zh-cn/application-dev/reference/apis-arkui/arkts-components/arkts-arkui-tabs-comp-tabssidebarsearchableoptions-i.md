# TabsSidebarSearchableOptions

```TypeScript
declare interface TabsSidebarSearchableOptions
```

定义可搜索侧边栏标签栏的选项。

**起始版本：** 26.0.1

<!--Device-unnamed-declare interface TabsSidebarSearchableOptions--><!--Device-unnamed-declare interface TabsSidebarSearchableOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## searchCallback

```TypeScript
searchCallback?: (text: string) => void
```

当搜索文本发生变化时触发的回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabsSidebarSearchableOptions-searchCallback?: (text: string) => void--><!--Device-TabsSidebarSearchableOptions-searchCallback?: (text: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | The current search text. |

## searchFilter

```TypeScript
searchFilter?: TabsSidebarSearchFilterCallback
```

过滤器函数，用于根据搜索文本确定是否应显示选项卡。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabsSidebarSearchableOptions-searchFilter?: TabsSidebarSearchFilterCallback--><!--Device-TabsSidebarSearchableOptions-searchFilter?: TabsSidebarSearchFilterCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

搜索输入为空时显示的占位符文本。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabsSidebarSearchableOptions-placeholder?: ResourceStr--><!--Device-TabsSidebarSearchableOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## searchText

```TypeScript
searchText?: ResourceStr
```

设置搜索文本框中的文本输入。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-TabsSidebarSearchableOptions-searchText?: ResourceStr--><!--Device-TabsSidebarSearchableOptions-searchText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
