# postCardAction

## postCardAction

```TypeScript
declare function postCardAction(component: Object, action: Object): void
```

Post Card Action.

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare function postCardAction(component: Object, action: Object): void--><!--Device-unnamed-declare function postCardAction(component: Object, action: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | Object | 是 | indicate the card entry component. |
| action | Object | 是 | indicate the router, message or call event.<!--Del-->Since API version 26.0.1, for system applications,the action support insightIntent event.<!--DelEnd--> |
