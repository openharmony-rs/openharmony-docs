# DynamicComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=fd10fbb9e5b5e2e1e561a46b9ca4925a29d1a0a3 translatedAt=2026-06-30T12:26:01.088Z pushedAt=2026-07-02T09:00:17.598Z -->

**DynamicComponent** is designed to support the embedding and display of UIs provided by independent .abc files within the current page, with the displayed content running in a worker thread.

It is typically used in modular development scenarios where .abc pages are dynamically loaded.

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
| options | [DynamicOptions](#dynamicoptions) | Yes| Configuration parameters for constructing a **DynamicComponent**, which are used to configure the entry of the .abc page to be loaded, worker thread to run, and display options.|

## Worker

type Worker = Worker

Defines the worker thread object for running the .abc file.

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

**Parameters**

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | No | No | Entry point of the .abc page to load. |
| worker | [Worker](#worker) | No| No| Worker for running the .abc file.|
| backgroundTransparent | boolean | No| Yes| Whether to enable the transparent background for the component.<br>**true**: yes; **false**: no.<br>The default value is **false**.|
| allowCrossProcessNesting | boolean | No| Yes| Whether to allow cross-process [UIExtensionComponent](./ts-container-ui-extension-component-sys.md) nesting.<br>**true**: yes; **false**: no.<br>The default value is **false**.|

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

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
  private worker?: worker.ThreadWorker = new worker.ThreadWorker(
    "entry/ets/workers/Worker.ets", { name: "dc-worker" }
  )

  aboutToDisappear() {
    this.worker?.terminate();
  }

  build() {
    Column() {
      Text('DynamicComponent Example').fontSize(20).margin(10)

      if (this.errorMessage) {
        Text('Error message: ' + this.errorMessage).fontSize(14).fontColor(Color.Red).margin(10)
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