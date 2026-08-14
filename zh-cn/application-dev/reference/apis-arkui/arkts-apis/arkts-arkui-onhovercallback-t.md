# OnHoverCallback

```TypeScript
export type OnHoverCallback = (status: boolean, event: HoverEvent) => void
```

鼠标悬浮触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnHoverCallback = (status: boolean, event: HoverEvent) => void--><!--Device-unnamed-export type OnHoverCallback = (status: boolean, event: HoverEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 表示鼠标是否悬浮在组件上，鼠标进入组件时为true，离开组件时为false。 |
| event | [HoverEvent](../arkts-components/arkts-arkui-hoverevent-i.md) | 是 | 设置悬浮事件。 |

