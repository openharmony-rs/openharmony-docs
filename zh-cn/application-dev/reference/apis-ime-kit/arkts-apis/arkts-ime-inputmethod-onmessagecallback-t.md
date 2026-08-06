# OnMessageCallback

```TypeScript
type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void
```

Callback function on receiving a custom message.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputMethod-type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void--><!--Device-inputMethod-type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | the identifier of the message.  |
| msgParam | ArrayBuffer | 否 | the parameter of the custom message.  |

