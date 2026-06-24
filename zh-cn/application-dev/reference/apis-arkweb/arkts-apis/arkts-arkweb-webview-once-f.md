# once

## once

```TypeScript
function once(type: string, callback: Callback<void>): void
```

Subscribe to a callback of a specified type of web event once.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | Types of web event. |
| callback | Callback&lt;void&gt; | 是 | Indicate callback used to receive the web event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';

webview.once("webInited", () => {
  console.info("configCookieSync");
  webview.WebCookieManager.configCookieSync("https://www.example.com", "a=b");
})

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

