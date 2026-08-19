# OnVerifyPinCallback

```TypeScript
export type OnVerifyPinCallback = (verifyPinEvent: VerifyPinEvent) => void
```

The callback of verify pin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnVerifyPinCallback = (verifyPinEvent: VerifyPinEvent) => void--><!--Device-unnamed-export type OnVerifyPinCallback = (verifyPinEvent: VerifyPinEvent) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| verifyPinEvent | [VerifyPinEvent](arkts-na-web-verifypinevent-i.md) | 是 | The event of verify PIN. |

