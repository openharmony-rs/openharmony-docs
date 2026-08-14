# HandleMemberPurchaseEvent

```TypeScript
type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise<DialogInfo>
```

处理购买会员事件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise<DialogInfo>--><!--Device-avMusicTemplate-type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise<DialogInfo>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [MemberPurchaseInfo](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md)&gt; | Promise对象，返回对话框信息。 |

