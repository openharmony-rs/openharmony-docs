# OnHoverCallback

```TypeScript
declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void
```

鼠标悬浮触发回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void--><!--Device-unnamed-declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 表示鼠标是否悬浮在组件上。true表示鼠标悬浮在组件上，false表示鼠标离开组件。  |
| event | [HoverEvent](arkts-arkui-hoverevent-i.md) | 是 | 鼠标悬浮事件对象，包含悬浮事件的详细信息（如鼠标位置等）。  |

