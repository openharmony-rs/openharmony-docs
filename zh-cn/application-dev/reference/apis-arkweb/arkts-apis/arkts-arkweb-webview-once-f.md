# once

## 导入模块

```TypeScript
```

## once

```TypeScript
function once(type: string, callback: Callback<void>): void
```

订阅一次指定类型Web事件的回调，Web事件的类型目前仅支持"webInited"，在Web引擎初始化完成时触发。当应用中开始加载第一个Web组件时，Web引擎初始化，且后续在同一应用中继续加载其他Web组件时不会再触发once回调。当应用销毁最后一个Web组件时，若再加载第一个Web组件，应用重新进入Web引擎初始化流程。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Web事件的类型，目前仅支持："webInited"（Web引擎初始化完成）。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | Web引擎初始化完成时触发的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

**示例**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';

webview.once('webInited', () => {
  console.info('configCookieSync');
  webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b');
});

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```
