# WebKeyboardOptions

Return value of the callback that intercepts the soft keyboard started from editable elements on the web page, including the keyboard type and custom keyboard. It is suitable for scenarios where controlling soft keyboard behavior is required.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## customKeyboard

```TypeScript
customKeyboard?: CustomBuilder
```

Builder of a custom keyboard. This parameter is required when **useSystemKeyboard** is set to **false**. After it is set, the **Web** component starts the custom keyboard as configured.

**Type:** [CustomBuilder](../../apis-arkui/arkts-components/arkts-arkui-custombuilder-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## enterKeyType

```TypeScript
enterKeyType?: number
```

Type of the **Enter** key on the system soft keyboard. For details about the value range, see [EnterKeyType](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-enterkeytype-e.md). This parameter is optional and the default value is **UNSPECIFIED**. This parameter is valid only when **useSystemKeyboard** is set to **true** and **enterKeyType** is set to a valid value.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## useSystemKeyboard

```TypeScript
useSystemKeyboard: boolean
```

Whether to use the system's default soft keyboard.

The value **true** means to use the system's default soft keyboard, and **false** means the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
