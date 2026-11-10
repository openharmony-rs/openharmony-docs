# TabsSidebarSearchFilterCallback

```TypeScript
declare type TabsSidebarSearchFilterCallback = (tabIndex: number, text: string) => boolean
```

定义可搜索侧边栏标签栏的选项。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare type TabsSidebarSearchFilterCallback = (tabIndex: number, text: string) => boolean--><!--Device-unnamed-declare type TabsSidebarSearchFilterCallback = (tabIndex: number, text: string) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabIndex | number | 是 | 要筛选的选项卡的索引。 |
| text | string | 是 | 当前搜索文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果选项卡与搜索条件匹配，则返回**true**，否则返回**false**。 |
