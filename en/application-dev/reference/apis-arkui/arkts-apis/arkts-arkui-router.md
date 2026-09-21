# @ohos.router

The **Router** module provides APIs to access pages through URLs. You can use the APIs to navigate to a specified page in an application, replace the current page with another one in the same application, and return to the previous page or a specified page.

For routing management, it is recommended that you use the [Navigation](../../../ui/arkts-navigation-architecture.md) component instead as your application routing framework.

> **NOTE:** 
> 
> - Page routing APIs can be invoked only after page rendering is complete. Do not call these APIs in **onInit** and
> **onReady** when the page is still in the rendering phase.
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).
> 
> - When using [pushUrl](arkts-arkui-arkui-uicontext-router-c.md#pushurl)or [pushNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#pushnamedroute)with a callback to return the result, be aware that the stack information obtained through the callback using APIs such as [getLength](arkts-arkui-arkui-uicontext-router-c.md#getlength) represents an intermediate state during the navigation operation. This temporary state might differ from the final stack information available after the stack operation is complete.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [back](arkts-arkui-router-back-f.md#back) | Returns to the previous page or a specified page, which deletes all pages between the current page and the target page. |
| [back](arkts-arkui-router-back-f.md#back-1) | Returns to the specified page, which deletes all pages between the current page and the target page. |
| [clear](arkts-arkui-router-clear-f.md) | Clears all historical pages in the stack and retains only the current page at the top of the stack. |
| [disableAlertBeforeBackPage](arkts-arkui-router-disablealertbeforebackpage-f.md) | Disables the display of a confirm dialog box before returning to the previous page. |
| [enableAlertBeforeBackPage](arkts-arkui-router-enablealertbeforebackpage-f.md) | Enables the display of a confirm dialog box before returning to the previous page. |
| [getLength](arkts-arkui-router-getlength-f.md) | Obtains the number of pages in the current stack. |
| [getParams](arkts-arkui-router-getparams-f.md) | Obtains the parameters passed from the page that initiates redirection to the current page. |
| [getState](arkts-arkui-router-getstate-f.md) | Obtains state information about the page at the top of the navigation stack. |
| [getStateByIndex](arkts-arkui-router-getstatebyindex-f.md) | Obtains the status information about a page by its index. |
| [getStateByUrl](arkts-arkui-router-getstatebyurl-f.md) | Obtains the status information about a page by its URL. |
| [hideAlertBeforeBackPage](arkts-arkui-router-hidealertbeforebackpage-f.md) | Disables the display of a confirm dialog box before returning to the previous page. |
| [push](arkts-arkui-router-push-f.md) | Navigates to a specified page in the application. |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushnamedroute) | Navigates to a page using the named route. This API uses a promise to return the result. |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushnamedroute-1) | Navigates to a page using the named route. This API uses a promise to return the result. |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushnamedroute-2) | Navigates to a page using the named route. This API uses a promise to return the result. |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushnamedroute-3) | Navigates to a page using the named route. This API uses a promise to return the result. |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushurl) | Navigates to a specified page in the application. |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushurl-1) | Navigates to a specified page in the application. |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushurl-2) | Navigates to a specified page in the application. |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushurl-3) | Navigates to a specified page in the application. |
| [replace](arkts-arkui-router-replace-f.md) | Replaces the current page with another one in the application and destroys the current page. |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replacenamedroute) | Replaces the current page with another one using the named route and destroys the current page. |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replacenamedroute-1) | Replaces the current page with another one using the named route and destroys the current page. |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replacenamedroute-2) | Replaces the current page with another one using the named route and destroys the current page. |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replacenamedroute-3) | Replaces the current page with another one using the named route and destroys the current page. |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceurl) | Replaces the current page with another one in the application and destroys the current page. |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceurl-1) | Replaces the current page with another one in the application and destroys the current page. This API cannot be used to configure page transition effects. To configure page transition effects, use the [Navigation](../../../ui/arkts-navigation-architecture.md) component. |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceurl-2) | Replaces the current page with another one in the application and destroys the current page. |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceurl-3) | Replaces the current page with another one in the application and destroys the current page. |
| [showAlertBeforeBackPage](arkts-arkui-router-showalertbeforebackpage-f.md) | Enables the display of a confirm dialog box before returning to the previous page. |

### Interfaces

| Name | Description |
| --- | --- |
| [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | Describes the page routing state. |
| [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | Describes the named route options. |
| [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Describes the page routing options. |
| [RouterState](arkts-arkui-router-routerstate-i.md) | Describes the page routing state. |

### Enums

| Name | Description |
| --- | --- |
| [RouterMode](arkts-arkui-router-routermode-e.md) | Enumerates the routing modes. |

## Examples

### JavaScript-based Web-like Development Paradigm

The following sample code applies only to JavaScript files, not ArkTS files.

```TypeScript
// Current page
export default {
  pushPage() {
    router.pushUrl({
      url: 'pages/detail/detail',
      params: {
        data1: 'message'
      }
    });
  }
}
```

```TypeScript
// detail page
export default {
  onInit() {
    console.info('showData1:' + router.getParams()['data1']);
  }
}
```

### TypeScript-based Declarative Development Paradigm

> NOTE
> 
> Directly using router can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain a [UIContext](arkts-apis-uicontext-uicontext.md) instance using getUIContext, and then obtain the associated router object using [getRouter](arkts-arkui-arkui-uicontext-uicontext-c.md#getrouter).

```TypeScript
// Navigate to the target page through router.pushUrl with the params parameter carried.
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the class for passing parameters.
class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class RouterParams {
  text: string;
  data: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Index {
  async routePage() {
    let options: router.RouterOptions = {
      url: 'pages/second',
      params: new RouterParams('This is the value on the first page', [12, 45, 78])
    };
    // You are advised to use this.getUIContext().getRouter().pushUrl().
    this.getUIContext().getRouter().pushUrl(options)
      .then(() => {
        console.info(`pushUrl finish`);
      })
      .catch((err: BusinessError) => {
        console.error(`pushUrl failed. Code: ${err.code}, message: ${err.message}`);
      })
    }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('This is the first page.')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage()
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
// Receive the transferred parameters on the second page.
import { router } from '@kit.ArkUI';

class InnerParams {
  array: number[];

  constructor(tuple: number[]) {
    this.array = tuple;
  }
}

class RouterParams {
  text: string;
  data: InnerParams;

  constructor(str: string, tuple: number[]) {
    this.text = str;
    this.data = new InnerParams(tuple);
  }
}

@Entry
@Component
struct Second {
  private content: string = 'This is the second page.';
  // You are advised to use this.getUIContext().getRouter().getParams().
  @State text: string = (this.getUIContext().getRouter().getParams() as RouterParams).text;
  @State data: InnerParams = (this.getUIContext().getRouter().getParams() as RouterParams).data;
  @State secondData: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text(`${this.content}`)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      Text(this.text)
        .fontSize(30)
        .onClick(() => {
          this.secondData = (this.data.array[1]).toString();
        })
        .margin({ top: 20 })
      Text(`This is the data passed from the first page: ${this.secondData}`)
        .fontSize(20)
        .margin({ top: 20 })
        .backgroundColor('red')
    }
    .width('100%')
    .height('100%')
  }
}
```

This example shows the redirection features of the router.replace and router.replaceUrl APIs in the web-like paradigm.

The following describes the tree structure:

```TypeScript
pages
├─ index
│  ├─ index.css
│  ├─ index.hml
│  └─ index.js
└─ routerPages
   ├─ routerPage.css
   ├─ routerPage.hml
   └─ routerPage.js
```

```TypeScript
/* index.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  border-radius: 21px;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}

.action-button-primary {
  margin-top: 22px;
  background-color: #2563eb;
}

.action-button-secondary {
  margin-top: 10px;
  background-color: #16a34a;
}
```

```TypeScript
<!--index.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button action-button-primary" type="button" value="replace to routerPage" onclick="replaceToRouterPage"></input>
    <input class="action-button action-button-secondary" type="button" value="replaceUrl to routerPage" onclick="replaceUrlToRouterPage"></input>
</div>
```

```TypeScript
// index.js
import { router } from '@kit.ArkUI';

export default {
    data: {
        pageName: 'Index Page',
        tips: 'Use replace or replaceUrl to open routerPage.',
        statusText: 'Current page: index'
    },
    replaceToRouterPage: function() {
        router.replace({
            url: 'pages/routerPages/routerPage',
            params: {
                statusText: 'Opened by router.replace.'
            }
        });
    },
    replaceUrlToRouterPage: function() {
        router.replaceUrl({
            url: 'pages/routerPages/routerPage',
            params: {
                statusText: 'Opened by router.replaceUrl.'
            }
        });
    }
}
```

```TypeScript
/* routerPage.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  border-radius: 21px;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}

.action-button-primary {
  margin-top: 22px;
  background-color: #2563eb;
}

.action-button-secondary {
  margin-top: 10px;
  background-color: #16a34a;
}
```

```TypeScript
<!--routerPage.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button action-button-primary" type="button" value="replace to index" onclick="replaceToIndex"></input>
    <input class="action-button action-button-secondary" type="button" value="replaceUrl to index" onclick="replaceUrlToIndex"></input>
</div>
```

```TypeScript
// routerPage.js
import { router } from '@kit.ArkUI';

export default {
    data: {
        pageName: 'Router Page',
        tips: 'Use replace or replaceUrl to return to index.',
        statusText: 'Current page: routerPage'
    },
    replaceToIndex: function() {
        router.replace({
            url: 'pages/index/index',
            params: {
                statusText: 'Returned by router.replace.'
            }
        });
    },
    replaceUrlToIndex: function() {
        router.replaceUrl({
            url: 'pages/index/index',
            params: {
                statusText: 'Returned by router.replaceUrl.'
            }
        });
    }
}
```
