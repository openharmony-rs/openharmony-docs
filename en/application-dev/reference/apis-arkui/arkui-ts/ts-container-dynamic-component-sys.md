# DynamicComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ef5506642718b24289c6aa216632b7a5e19e795e translatedAt=2026-08-21T02:22:42.372Z pushedAt=2026-08-21T07:27:56.358Z -->

**DynamicComponent** is designed to support the embedding and display of UIs provided by independent Abc (Ark bytecode, .abc files) within the current page, with the displayed content running in a worker thread.

It is typically used in modular development scenarios where .abc pages are dynamically loaded. The .abc UI runs in isolation in a worker thread, preventing the main thread from being blocked and improving app smoothness.

> **NOTE**
>
> - The APIs provided by this module are system APIs.
> - The APIs of this module can be used only in the stage model.

**Since:** 26.0.0

## Child Components

None

## APIs

DynamicComponent(options: DynamicOptions)

Creates a **DynamicComponent** component to display the .abc UI running in the worker thread.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | Yes | Configuration parameters for constructing a **DynamicComponent**, which are used to configure the entry of the .abc page to be loaded, worker thread to run, display options, and cross-process nesting. |

## Worker

type Worker = Worker

Worker thread object used to run .abc. It must be created through **worker.ThreadWorker**.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| -------- | -------- |
| [Worker](../../apis-arkts/js-apis-worker.md) | An independent thread that runs the .abc file.|

## ErrorCallback

type ErrorCallback = ErrorCallback

Defines the error callback type, which is used to receive exception information.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| -------- | -------- |
| [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Callback used to receive exception information during running.|

## DynamicOptions

Defines the parameters to be passed during **DynamicComponent** construction.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | No | No | The .abc page entry to load. The value format is 'bundleName/moduleName/pagePath', for example, 'com.example.myapplication/entry/ets/pages/DynamicPage'. |
| worker | [Worker](#worker) | No | No | Worker thread object used to run the .abc, which must be created through **worker.ThreadWorker**. The Worker executes the UI logic of the .abc in an independent thread and communicates with the main thread. |
| backgroundTransparent | boolean | No | Yes | Whether to enable background transparency for the component.<br>**true**: enable background transparency; **false**: disable background transparency.<br>Default value: **false** |
| allowCrossProcessNesting | boolean | No | Yes | Whether to allow cross-process [UIExtensionComponent](./ts-container-ui-extension-component-sys.md) nesting.<br>**true**: allow cross-process nesting; **false**: disallow cross-process nesting.<br>Default value: **false** |
| allowOccupied | boolean | No | Yes | Whether to allow the **DynamicComponent** to avoid the keyboard internally.<br>**true**: allow avoiding the keyboard; **false**: do not allow avoiding the keyboard.<br>Default value: **false** |

## Attributes

[Universal attributes](./ts-component-general-attributes.md) are supported.

## Events

The following events are supported:

### onError

onError(callback: ErrorCallback)

Triggered when an exception occurs during the running of the **DynamicComponent**. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback used to receive exception information.|

## Example

### Example 1: Loading an Independent .abc Page and Listening for Runtime Exceptions

This example demonstrates the basic usage of **DynamicComponent**. It loads an .abc page running in a specified worker thread by configuring [DynamicOptions](#dynamicoptions), and handles runtime exceptions through the [onError](#onerror) callback.

Since API version 26.0.0, the [onError](#onerror) event is added.

``` TypeScript
import { worker } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State errorMessage: string = '';
  private worker: worker.ThreadWorker = new worker.ThreadWorker(
    'entry/ets/workers/Worker.ets', { name: 'dc-worker' }
  );

  aboutToDisappear() {
    this.worker?.terminate();
  }

  build() {
    Column() {
      Text('DynamicComponent Example').fontSize(20).margin(10)

      if (this.errorMessage) {
        Text('Error message:' + this.errorMessage).fontSize(14).fontColor(Color.Red).margin(10)
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
          console.error(`onError: code: ${error.code}, message: ${error.message}`);
        })
        .borderWidth(10)
        .borderColor(Color.Red)
    }
    .height('100%')
    .width('100%')
  }
}
```

- The following is the implementation file **/src/main/ets/workers/Worker.ets** for the worker thread object used to run the .abc file.

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

- The embedded .abc page **/src/main/ets/pages/DynamicPage.ets**.

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

- Configure the route for the provider page in **main_pages.json**.

  ``` JSON
  {
    "src": [
      "pages/Index",
      "pages/DynamicPage"
    ]
  }
  ```