# Interface (BackForwardList)

当前Webview的历史信息列表。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Interface首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 导入模块

```ts
import { webview } from '@kit.ArkWeb';
```

## 属性

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称         | 类型   | 只读 | 可选 | 说明                                                         |
| ------------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| currentIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 否   | 当前在页面历史列表中的索引。                                 |
| size         | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 否   | 历史列表中索引的数量，最多保存50条，超过时起始记录会被覆盖。 |

## getItemAtIndex

ArkTS-Dyn: getItemAtIndex(index: number): HistoryItem

ArkTS-Sta: getItemAtIndex(index: int): HistoryItem

获取历史列表中指定索引的历史记录项信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                   |
| ------ | ------ | ---- | ---------------------- |
| index  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 指定历史列表中的索引。 |

**返回值：**

| 类型                        | 说明         |
| --------------------------- | ------------ |
| [HistoryItem](./arkts-apis-webview-i.md#historyitem) | 历史记录项。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  @State icon: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Button('getBackForwardEntries')
        .onClick(() => {
          try {
            let list = this.controller.getBackForwardEntries();
            let historyItem = list.getItemAtIndex(list.currentIndex);
            console.info("HistoryItem: " + JSON.stringify(historyItem));
            this.icon = historyItem.icon;
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
```ts
// xxx.ets
'use static'
import { State, Entry, Column, Component, Web, Button } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  @State icon: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Button('getBackForwardEntries')
        .onClick(() => {
          try {
            let list = this.controller.getBackForwardEntries();
            let historyItem = list.getItemAtIndex(list.currentIndex);
            console.info("HistoryItem: " + JSON.stringify(historyItem));
            this.icon = historyItem.icon;
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## 使用@ohos.transfer进行BackForwardList类型转换

ArkTS-Dyn中使用ArkTS-Sta的BackForwardList对象。

- 在ArkTS-Sta模块中将ArkTS-Sta BackForwardList转换成ArkTS-Dyn BackForwardList，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { BackforwardListStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("BackForwardList")
          .onClick(() => {
            try {
              let list = this.controller.getBackForwardEntries();
              let dynamicHandler = transfer.transferDynamic(list, 'ArkWeb.BackForwardList');
              BackforwardListStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.baidu.com", controller: this.controller })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn BackForwardList的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { webview } from '@kit.ArkWeb';
  export function BackforwardListStaticToDynamic(handler_: any) {
    try {
      let handler: webview.BackForwardList = handler_ as webview.BackForwardList;
      console.info('BackforwardListStaticToDynamic size=' + handler.size);
    } catch (e) {
      console.error('BackforwardListStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的BackForwardList对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn BackForwardList对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { BackforwardListDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("BackForwardList")
          .onClick(() => {
            try {
              let list = this.controller.getBackForwardEntries();
              BackforwardListDynamicToStatic(list);
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: "www.baidu.com", controller: this.controller })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn BackForwardList的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';

  export function BackforwardListDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: webview.BackForwardList = transfer.transferStatic(dynObject, 'ArkWeb.BackForwardList') as webview.BackForwardList;
        console.info('BackforwardListDynamicToStatic size=' + handler.size);
    } catch (e: Error) {
        console.error('BackforwardListDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```