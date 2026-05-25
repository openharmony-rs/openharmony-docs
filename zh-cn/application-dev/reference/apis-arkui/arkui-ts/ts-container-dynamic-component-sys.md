# DynamicComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

DynamicComponent用于支持在本页面内嵌入显示独立Abc（.abc文件）提供的UI，展示的内容在Worker线程中运行。

通常用于动态加载Abc页面的模块化开发场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块为系统接口。
>
> - 本模块接口仅可在Stage模型下使用。

 **起始版本：** 26.0.0

## 子组件

无

## 接口

DynamicComponent(options: DynamicOptions)

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | 是 | DynamicComponent的构造配置参数，用于配置要加载的Abc页面入口、运行Worker及显示选项。 |

## Worker

type Worker = Worker

用于运行Abc的Worker线程对象。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| -------- | -------- |
| [Worker](../../apis-arkts/js-apis-worker.md) | 用于在独立线程中运行Abc。 |

## ErrorCallback

type ErrorCallback = ErrorCallback

错误回调类型，用于接收异常信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| -------- | -------- |
| [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | 用于接收运行过程中的异常信息。 |

## DynamicOptions

用于在DynamicComponent构造时传递参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | 否 | 否 | 要加载的abc页面入口。 |
| worker | ArkTS-Dyn: [Worker](#worker)<br/>ArkTS-Sta: EAWorker \| undefined | 否 | ArkTS-Dyn: 否<br/>ArkTS-Sta: 是 | 运行Abc的Worker。<br/>ArkTS-Sta模式下，undefined回拉起一个空的DynamicComponent。<br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0 |
| backgroundTransparent | boolean | 否 | 是 | 是否启用组件背景透明。<br/>true：启用背景透明；false：不启用背景透明。<br/>默认值：false <br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0 |
| allowCrossProcessNesting | boolean | 否 | 是 | 是否允许跨进程[UIExtensionComponent](./ts-container-ui-extension-component-sys.md)嵌套。<br/>true：允许跨进程嵌套；false：不允许跨进程嵌套。<br/>默认值：false <br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0 |
| allowOccupied | boolean | 否 | 是 | 是否允许DynamicComponent占用键盘避让区域。<br/>true：允许占用键盘避让区域；false：不允许占用键盘避让区域。<br/>默认值：false<br/> **ArkTS模式：** 该接口仅适用于ArkTS-Sta<br/>**ArkTS-Sta起始版本：** 26.0.0 |

## 属性

支持[通用属性](ts-component-general-attributes.md)。

## 事件

支持以下事件：

### onError

ArkTS-Dyn: onError(callback: ErrorCallback)

ArkTS-Sta: onError(callback: ErrorCallback\<BusinessError\> | undefined)

DynamicComponent运行过程中发生异常时触发该回调。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [ErrorCallback](#errorcallback)<br/>ArkTS-Sta: [ErrorCallback](#errorcallback)\<[BusinessError](../../apis-basic-services-kit/js-apis-base.md#businesserror)> \| undefined | 是 | 回调函数，入参用于接收异常信息。<br/>ArkTS-Sta模式下，可传入undefined，表示取消回调函数。 |

## 示例

### 示例1（加载独立Abc页面并监听运行异常）

本示例展示了DynamicComponent的基本用法，通过配置[DynamicOptions](#dynamicoptions)加载指定Worker线程中运行的Abc页面，并通过[onError](#onerror)回调处理运行异常。

从API版本26.0.0开始，新增[onError](#onerror)事件。

ArkTS-Dyn示例：

``` TypeScript
import { worker } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State errorMessage: string = '';
  private worker?: worker.ThreadWorker = new worker.ThreadWorker(
    'entry/ets/workers/Worker.ets', { name: 'dc-worker' }
  )

  build() {
    Column() {
      Text('DynamicComponent示例').fontSize(20).margin(10)

      if (this.errorMessage) {
        Text('错误信息: ' + this.errorMessage).fontSize(14).fontColor(Color.Red).margin(10)
      }

      DynamicComponent({
        entryPoint: 'com.example.myapplication/entry/ets/pages/DynamicPage',
        worker: this.worker,
        backgroundTransparent: false,
        allowCrossProcessNesting: false
      })
        .width('100%')
        .height('60%')
        .onError((error: BusinessError) => {
          this.errorMessage = `code: ${error.code}, message: ${error.message}`;
          hilog.error(0x0000, 'DynamicComponentDemo', 'onError: ' + this.errorMessage);
        })
        .borderWidth(10)
        .borderColor(Color.Red)
    }
    .height('100%')
    .width('100%')
  }
}
```

- 以下为用于运行Abc的Worker线程对象的实现文件`/src/main/ets/workers/Worker.ets`。

  ```ts
  import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

  const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

  workerPort.onmessage = (event: MessageEvents) => {
  };

  workerPort.onmessageerror = (event: MessageEvents) => {
  };

  workerPort.onerror = (event: ErrorEvent) => {
  };
  ```

- 嵌入显示的Abc页面`/src/main/ets/pages/DynamicPage.ets`。

  ``` TypeScript
  @Entry
  @Component
  struct DynamicPage {
    build() {
      Column() {
        Text('this is ability in DC')
          .fontSize(20)
          .margin(10)
      }
      .height('100%')
      .width('100%')
      .borderWidth(10)
      .borderColor(Color.Blue)
      .align(Alignment.Top)
    }
  }
  ```

- 为提供方页面配置路由`main_pages.json`。

  ``` JSON
  {
    "src": [
      "pages/Index",
      "pages/DynamicPage"
    ]
  }
  ```

ArkTS-Sta示例：

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { State } from '@ohos.arkui.stateManagement';
import { Column, Text, Component, Entry, DynamicComponent, Color } from '@ohos.arkui.component';

@Entry
@Component
struct Index {
  @State errorMessage: string = '';
  @State worker: EAWorker = new EAWorker(true);

  build() {
    Column() {
      Text('DynamicComponent示例').fontSize(20).margin(10)

      if (this.errorMessage) {
        Text('错误信息: ' + this.errorMessage).fontSize(14).fontColor(Color.Red).margin(10)
      }

      DynamicComponent({
        entryPoint: 'com.example.myapplication/entry/ets/pages/DynamicPage',
        worker: this.worker!,
        backgroundTransparent: false,
        allowCrossProcessNesting: false,
        allowOccupied: false,
      })
        .width('100%')
        .height('60%')
        .onError((error: BusinessError) => {
          this.errorMessage = `code: ${error.code}, message: ${error.message}`;
          hilog.error(0x0000, 'DynamicComponentDemo', 'onError: ' + this.errorMessage);
        })
        .borderWidth(10)
        .borderColor(Color.Red)
    }
    .height('100%')
    .width('100%')
  }
}
```

- 嵌入显示的Abc页面`/src/main/ets/pages/DynamicPage.ets`。

  ``` TypeScript
  import { Column, Text, Component, Entry, Color } from '@ohos.arkui.component';
  
  @Entry
  @Component
  struct DynamicPage {
    build() {
      Column() {
        Text('this is ability in DC')
          .fontSize(20)
          .margin(10)
      }
      .height('100%')
      .width('100%')
      .borderWidth(10)
      .borderColor(Color.Blue)
      .align(Alignment.Top)
    }
  }
  ```

- 为提供方页面配置路由`main_pages.json`。

  ``` JSON
  {
    "src": [
      "pages/Index",
      "pages/DynamicPage"
    ]
  }
  ```
