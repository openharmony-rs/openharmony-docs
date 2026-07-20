# SearchSubmitCallback

```TypeScript
declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void
```

点击搜索图标、搜索按钮或者按下软键盘搜索按钮时的回调事件。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void--><!--Device-unnamed-declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchContent | string | 是 | 当前搜索框中输入的文本内容。  |
| event | [SubmitEvent](arkts-arkui-submitevent-i.md) | 否 | 提交事件。  |

