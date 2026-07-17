# registerWebAdInterface

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## registerWebAdInterface

```TypeScript
function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void
```

注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-advertising-function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void--><!--Device-advertising-function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | web_webview.WebviewController | 是 | Web组件控制器。 |
| context | common.UIAbilityContext | 是 | UIAbility的上下文环境。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context);
        })
      // ...

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}

```


## registerWebAdInterface

```TypeScript
function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, 
    needRefresh: boolean): void
```

注入广告JavaScript对象到Web组件中（该接口仅对部分系统预置应用开放）。

**起始版本：** 16

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务API中使用。

<!--Device-advertising-function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, 
    needRefresh: boolean): void--><!--Device-advertising-function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, 
    needRefresh: boolean): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | web_webview.WebviewController | 是 | Web组件控制器。 |
| context | common.UIAbilityContext | 是 | UIAbility的上下文环境。 |
| needRefresh | boolean | 是 | 是否需要刷新页面（true: 需要；false: 不需要）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private webViewController: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      // ...
      Button('registerWebAdInterface')
        .onClick(() => {
          advertising.registerWebAdInterface(this.webViewController, this.context, true);
        })

      Web({ src: 'https://www.example.com', controller: this.webViewController })
    }
    .width('100%')
    .height('100%')
  }
}

```

