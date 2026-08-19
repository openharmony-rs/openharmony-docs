# WebKeyboardController

WebKeyboardController是ArkWeb提供的用于控制Web组件自定义键盘行为的控制器类。当Web页面中的输入框需要弹出键盘时，开发者可通过 [onInterceptKeyboardAttach](arkts-arkweb-web-attribute.md#oninterceptkeyboardattach)事件拦截系统默认键盘的挂载，并使用WebKeyboardController向当前聚焦的 Web输入框执行插入字符、前向/后向删除、发送Enter等功能键以及关闭自定义键盘等操作。该类适用于需要为Web场景实现自定义安全键盘、表情键盘、手写键盘或业务专属输入面板的应用，使开发者能够完全接管Web输入框的键盘输入逻辑。

**起始版本：** 12

<!--Device-unnamed-declare class WebKeyboardController--><!--Device-unnamed-declare class WebKeyboardController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## close

```TypeScript
close(): void
```

关闭自定义键盘。

**起始版本：** 12

<!--Device-WebKeyboardController-close(): void--><!--Device-WebKeyboardController-close(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebKeyboardController的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardController-constructor()--><!--Device-WebKeyboardController-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deleteBackward

```TypeScript
deleteBackward(length: number): void
```

删除光标后面的指定长度字符。

**起始版本：** 12

<!--Device-WebKeyboardController-deleteBackward(length: number): void--><!--Device-WebKeyboardController-deleteBackward(length: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 删除光标后面的指定长度字符。 <br>取值范围：[-2147483648 , 2147483647]，当参数值大于字符长度时，默认删除光标后面所有字符；参数值为负数时，不执行删除操作。 |

## deleteForward

```TypeScript
deleteForward(length: number): void
```

删除光标前面的指定长度字符。

**起始版本：** 12

<!--Device-WebKeyboardController-deleteForward(length: number): void--><!--Device-WebKeyboardController-deleteForward(length: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 删除光标前面的指定长度字符。 <br>取值范围：[-2147483648 , 2147483647]，当参数值大于字符长度时，默认删除光标前面所有字符；参数值为负数时，不执行删除操作。 |

## insertText

```TypeScript
insertText(text: string): void
```

Web输入框中插入字符。

**起始版本：** 12

<!--Device-WebKeyboardController-insertText(text: string): void--><!--Device-WebKeyboardController-insertText(text: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 在当前光标位置插入Web输入框的文本。若存在选中文本则替换为该文本；触发输入事件；光标移动到插入文本末尾。 |

## sendFunctionKey

```TypeScript
sendFunctionKey(key: number): void
```

插入功能按键，目前仅支持Enter键类型，取值见[EnterKeyType](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-enterkeytype-e.md)。

**起始版本：** 12

<!--Device-WebKeyboardController-sendFunctionKey(key: number): void--><!--Device-WebKeyboardController-sendFunctionKey(key: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 功能键类型，仅支持Enter键。 |

