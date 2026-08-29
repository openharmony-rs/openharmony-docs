# WebController

* WebController是ArkWeb组件的控制器类，用于控制Web组件的各种行为。一个WebController对象只能与一个Web组件绑定，绑定后开发者可通过该控制器对Web组件进行页面导航（前进/后退/加载）、焦点控制、缩放调 整、页面刷新与停止、Cookie管理、JavaScript注入与执行等操作。WebController适用于需要在应用侧对嵌入式Web组件进行主动控制的场景，例如实现浏览器式的前进后退导航、在应用侧与网页侧之间建立JavaScript交互通道、动态加载网页内容或管理Cookie数据。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** WebviewController

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## accessBackward

```TypeScript
accessBackward(): boolean
```

当前页面是否可后退，即当前页面是否有返回历史记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessBackward

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可以后退返回true，否则返回false。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('accessBackward')
        .onClick(() => {
          let result = this.controller.accessBackward()
          console.info('result:' + result)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## accessForward

```TypeScript
accessForward(): boolean
```

当前页面是否可前进，即当前页面是否有前进历史记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessForward

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前页面可以前进，返回false表示当前页面不可以前进。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('accessForward')
        .onClick(() => {
          let result = this.controller.accessForward()
          console.info('result:' + result)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## accessStep

```TypeScript
accessStep(step: number): boolean
```

检查当前页面是否可前进或者后退给定的step步。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessStep

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 要跳转的步数，正数代表前进，负数代表后退。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 页面是否可以前进或后退给定的step步。true表示可以，false为不可以。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()
  @State steps: number = 2

  build() {
    Column() {
      Button('accessStep')
        .onClick(() => {
          let result = this.controller.accessStep(this.steps)
          console.info('result:' + result)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## backward

```TypeScript
backward()
```

按照历史栈，后退一个页面。建议在调用backward前先调用 [accessBackward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessbackward)检查当前页面是否可后退。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** backward

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('backward')
        .onClick(() => {
          this.controller.backward()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearHistory

```TypeScript
clearHistory(): void
```

删除所有前进后退记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearHistory

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('clearHistory')
        .onClick(() => {
          this.controller.clearHistory()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## constructor

```TypeScript
constructor()
```

WebController的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

**系统能力：** SystemCapability.Web.Webview.Core

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string)
```

删除通过registerJavaScriptProxy注册到window上的指定name的应用侧JavaScript对象。删除后立即生效，无须调用[refresh](#refresh)接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteJavaScriptRegister

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 注册对象的名称，可在网页侧JavaScript中通过此名称调用应用侧JavaScript对象。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()
  @State name: string = 'Object'

  build() {
    Column() {
      Button('deleteJavaScriptRegister')
        .onClick(() => {
          this.controller.deleteJavaScriptRegister(this.name)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## forward

```TypeScript
forward()
```

按照历史栈，前进一个页面。建议在调用forward前先调用 [accessForward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessforward)检查当前页面是否可前进。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** forward

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('forward')
        .onClick(() => {
          this.controller.forward()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## getCookieManager

```TypeScript
getCookieManager(): WebCookie
```

获取Web组件cookie管理对象。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebCookie](arkts-arkweb-webcookie-c.md) | Web组件cookie管理对象，参考[WebCookie]{ |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('getCookieManager')
        .onClick(() => {
          let cookieManager = this.controller.getCookieManager()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## getHitTest

```TypeScript
getHitTest(): HitTestType
```

获取当前被点击区域的元素类型。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getHitTest](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#gethittest)

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestType](arkts-arkweb-hittesttype-e.md) | 被点击区域的元素类型。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('getHitTest')
        .onClick(() => {
          let hitType = this.controller.getHitTest()
          console.info("hitType: " + hitType)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## loadData

```TypeScript
loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })
```

baseUrl为空时，通过“data”协议加载指定的一段字符串。当baseUrl为“data”协议时，编码后的data字符串将被Web组件作为“data”协议加载。当baseUrl为“http/https”协议时，编码后的data字符串将被Web组件以类似loadUrl的方式以非编码字符串处理。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadData

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string } | 是 | The options with the data or URL and other information. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('loadData')
        .onClick(() => {
          this.controller.loadData({
            data: "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>",
            mimeType: "text/html",
            encoding: "UTF-8"
          })
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## loadUrl

```TypeScript
loadUrl(options: { url: string | Resource, headers?: Array<Header> })
```

使用指定的HTTP头加载指定的URL。通过loadUrl注入的对象只在当前document有效，即通过loadUrl导航到新的页面会无效。而通过registerJavaScriptProxy注入的对象，在loadUrl导航到新的页面也会有效。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadUrl

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { url: string \| Resource, headers?: Array&lt;[Header](arkts-arkweb-header-i.md)&gt; } | 是 | The options with the URL and other information. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('loadUrl')
        .onClick(() => {
          this.controller.loadUrl({ url: 'www.example.com' })
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## onActive

```TypeScript
onActive(): void
```

调用此接口通知Web组件进入前台激活状态。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onActive

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('onActive')
        .onClick(() => {
          this.controller.onActive()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## onInactive

```TypeScript
onInactive(): void
```

调用此接口通知Web组件进入未激活状态。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onInactive

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('onInactive')
        .onClick(() => {
          this.controller.onInactive()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## refresh

```TypeScript
refresh()
```

调用此接口通知Web组件刷新网页。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** refresh

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('refresh')
        .onClick(() => {
          this.controller.refresh()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })
```

注入JavaScript对象到window对象中，并在window对象中调用该对象的方法。注入的对象在页面下一次（重新）加载前不会出现在JavaScript中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** registerJavaScriptProxy

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { object: object, name: string, methodList: Array &lt;string&gt; } | 是 | The option with the JavaScript object and method list. |

**示例**

```TypeScript
// xxx.ets
class TestObj {
  constructor() {
  }

  test(): string {
    return "ArkUI Web Component"
  }

  toString(): void {
    console.info('Web Component toString')
  }
}

@Entry
@Component
struct Index {
  controller: WebController = new WebController()
  testObj = new TestObj();
  build() {
    Column() {
      Row() {
        Button('Register JavaScript To Window').onClick(() => {
          this.controller.registerJavaScriptProxy({
            object: this.testObj,
            name: "objName",
            methodList: ["test", "toString"],
          })
        })
      }
      Web({ src: $rawfile('index.html'), controller: this.controller })
        .javaScriptAccess(true)
    }
  }
}
```

加载的HTML文件。

```TypeScript
<!-- index.html -->
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        Hello world!
        <script type="text/javascript">
            function htmlTest() {
                str = objName.test("test function")
                console.info('objName.test result:'+ str)
            }
        </script>
    </body>
</html>
```

## requestFocus

```TypeScript
requestFocus()
```

使当前Web页面获取焦点。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** requestFocus

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('requestFocus')
        .onClick(() => {
          this.controller.requestFocus()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## runJavaScript

```TypeScript
runJavaScript(options: { script: string, callback?: (result: string) => void })
```

异步执行JavaScript脚本，并通过回调方式返回脚本执行的结果。runJavaScript需要在loadUrl完成后，比如onPageEnd中调用。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** runJavaScript

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { script: string, callback?: (result: string) =&gt; void } | 是 | The options with a piece of code and a callback. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()
  @State webResult: string = ''
  build() {
    Column() {
      Text(this.webResult).fontSize(20)
      Web({ src: $rawfile('index.html'), controller: this.controller })
      .javaScriptAccess(true)
      .onPageEnd((event) => {
        this.controller.runJavaScript({
          script: 'test()',
          callback: (result: string) => {
            this.webResult = result
            console.info(`The test() return value is: ${result}`)
          }})
        if (event) {
          console.info('url: ', event.url)
        }
      })
    }
  }
}
```

加载的HTML文件。

```TypeScript
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
      <meta charset="utf-8">
  </head>
  <body>
      Hello world!
      <script type="text/javascript">
          function test() {
              console.info('Ark WebComponent')
              return "This value is from index.html"
          }
      </script>
  </body>
</html>
```

## stop

```TypeScript
stop()
```

停止页面加载。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stop

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()

  build() {
    Column() {
      Button('stop')
        .onClick(() => {
          this.controller.stop()
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## zoom

```TypeScript
zoom(factor: number): void
```

调整当前网页的缩放比例。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [zoom](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#zoom)

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | The zoom factor. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct WebComponent {
  controller: WebController = new WebController()
  @State factor: number = 1

  build() {
    Column() {
      Button('zoom')
        .onClick(() => {
          this.controller.zoom(this.factor)
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```
