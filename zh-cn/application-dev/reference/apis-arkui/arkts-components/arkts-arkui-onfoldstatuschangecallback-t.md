# OnFoldStatusChangeCallback

```TypeScript
declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void
```

当折叠状态改变时触发的回调&lt;!--RP4--&gt;，仅在横屏状态下生效&lt;!--RP4End--&gt;。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void--><!--Device-unnamed-declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnFoldStatusChangeInfo](arkts-arkui-onfoldstatuschangeinfo-i.md) | 是 | 折叠状态改变时的信息，仅在横屏状态下生效。 |

