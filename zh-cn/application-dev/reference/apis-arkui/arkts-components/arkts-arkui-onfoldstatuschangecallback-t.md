# OnFoldStatusChangeCallback

```TypeScript
declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void
```

当折叠状态改变时触发的回调\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_，仅在横屏状态下生效\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void--><!--Device-unnamed-declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 折叠状态改变时的信息，仅在横屏状态下生效。  |

