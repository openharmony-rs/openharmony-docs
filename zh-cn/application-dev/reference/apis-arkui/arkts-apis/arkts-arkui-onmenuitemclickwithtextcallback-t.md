# OnMenuItemClickWithTextCallback

```TypeScript
export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean
```

点击菜单项时触发，可拦截系统默认菜单项（如复制、粘贴菜单项）的执行行为。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean--><!--Device-unnamed-export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItem | TextMenuItem | 是 | 当前点击的菜单项。 |
| value | string | 是 | 选中文本内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 菜单项点击事件的处理结果。返回true表示事件已处理，返回false表示未处理。 |

