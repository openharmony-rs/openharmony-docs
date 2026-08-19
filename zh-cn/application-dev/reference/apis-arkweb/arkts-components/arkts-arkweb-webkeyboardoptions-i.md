# WebKeyboardOptions

拦截网页可编辑元素拉起软键盘的回调返回值，包括键盘类型和自定义键盘。适用于需要控制软键盘行为的场景。

**起始版本：** 12

<!--Device-unnamed-declare interface WebKeyboardOptions--><!--Device-unnamed-declare interface WebKeyboardOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## customKeyboard

```TypeScript
customKeyboard?: CustomBuilder
```

指定自定义键盘组件builder，可选参数，当useSystemKeyboard为false时，需要设置该参数，然后Web组件会拉起该自定义键盘。

**类型：** CustomBuilder

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardOptions-customKeyboard?: CustomBuilder--><!--Device-WebKeyboardOptions-customKeyboard?: CustomBuilder-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enterKeyType

```TypeScript
enterKeyType?: number
```

指定系统软键盘enter键的类型，取值范围见输入框架的定义[EnterKeyType](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-enterkeytype-e.md)，该参数为可选参数，默认值为 UNSPECIFIED。当useSystemKeyboard为true，并且设置了有效的enterKeyType时候，才有效。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardOptions-enterKeyType?: number--><!--Device-WebKeyboardOptions-enterKeyType?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## useSystemKeyboard

```TypeScript
useSystemKeyboard: boolean
```

是否使用系统默认软键盘。 true表示使用系统默认软键盘，false表示不使用系统默认软键盘。 默认值：true。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardOptions-useSystemKeyboard: boolean--><!--Device-WebKeyboardOptions-useSystemKeyboard: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

