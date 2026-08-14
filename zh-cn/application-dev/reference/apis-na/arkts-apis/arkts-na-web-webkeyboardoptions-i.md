# WebKeyboardOptions

Defines the web keyboard options when onInterceptKeyboardAttach event return.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface WebKeyboardOptions--><!--Device-unnamed-export declare interface WebKeyboardOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## customKeyboard

```TypeScript
customKeyboard?: CustomBuilder
```

Set the custom keyboard builder when the custom keyboard is used.

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardOptions-customKeyboard?: CustomBuilder--><!--Device-WebKeyboardOptions-customKeyboard?: CustomBuilder-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enterKeyType

```TypeScript
enterKeyType?: int
```

Set the enter key type when the system keyboard is used, the "enter" key related to the [inputMethodEngine](../../apis-ime-kit/arkts-apis/arkts-inputmethodengine.md#@ohos.inputMethodEngine).

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardOptions-enterKeyType?: int--><!--Device-WebKeyboardOptions-enterKeyType?: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## useSystemKeyboard

```TypeScript
useSystemKeyboard: boolean
```

Whether the system keyboard is used.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardOptions-useSystemKeyboard: boolean--><!--Device-WebKeyboardOptions-useSystemKeyboard: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

