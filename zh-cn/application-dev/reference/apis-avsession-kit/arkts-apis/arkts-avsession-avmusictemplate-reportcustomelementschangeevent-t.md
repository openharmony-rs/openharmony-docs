# ReportCustomElementsChangeEvent

```TypeScript
type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType,
    customElement: CustomElement) => void
```

上报自定义元素变更信息的回调事件

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType,    customElement: CustomElement) => void--><!--Device-avMusicTemplate-type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType,    customElement: CustomElement) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 操作类型  |
| customType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 自定义信息类型  |
| customElement | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 自定义数据  |

