# IsolatedComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-21T02:24:23.263Z pushedAt=2026-08-21T08:34:50.234Z -->

**IsolatedComponent** is designed to support the embedding and display of UIs provided by independent .abc files (Ark bytecode) within the current page, with the displayed content running in a restricted Worker thread.

This component is primarily designed for modular development scenarios that require hot updates for .abc files. (The .abc files loaded by **IsolatedComponent** can be dynamically replaced, enabling content updates without reinstalling the app.)

> **NOTE**
>
> - This component is supported since API version 12. New APIs added in later versions will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs provided by this module are system APIs.

## Constraints

**Specifications Constraints**

1. This component does not support preview.

2. The .abc file must pass [verifyAbc](../../apis-ability-kit/js-apis-bundleManager-sys.md#bundlemanagerverifyabc11) verification before it can be used with this component, and the **ohos.permission.RUN_DYN_CODE** permission must be configured in **module.json5**.

3. Constructor parameter updates are not supported; only the initial input is effective.

4. Nesting of **IsolatedComponent** components is not supported.

**Experience Constraints**

1. When an **IsolatedComponent** component is created, there is a certain amount of time required for the restricted Worker thread to load and render the .abc file layout (the specific duration depends on the complexity of the .abc file). During this period, the background color of the **IsolatedComponent** is displayed.

2. The main thread and the restricted Worker thread handle layout rendering asynchronously, which can lead to desynchronization in page changes caused by layout alterations or rotations.

3. Event passing between the main thread and the restricted Worker thread is managed asynchronously, and there is no support for event bubbling between threads. As a result, UI interactions between threads may encounter event conflicts.

**Security Constraints**

1. Displaying an independent .abc file through the **IsolatedComponent** component in the host process means that the .abc file content is fully accessible to the host, granting the host the control over the content of the independent .abc file. Therefore, this component is prohibited in security-sensitive scenarios.

2. Running independent .abc files in a restricted Worker thread offers a level of security, as the .abc file content does not interfere with the main thread.

## Child Components

Not supported

## APIs

IsolatedComponent(options: IsolatedOptions)

Creates an **IsolatedComponent** component to display the .abc file executed in a restricted Worker thread.

> **NOTE**
>
> Constructor parameter updates are not supported; only the initial input is effective. Before use, ensure that the .abc file has passed [verifyAbc](../../apis-ability-kit/js-apis-bundleManager-sys.md#bundlemanagerverifyabc11) verification and that the **ohos.permission.RUN_DYN_CODE** permission has been configured in **module.json5**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                                  | Mandatory| Description          |
| --------------------- | ---------------------------------------------------------- | ---- | ------------------ |
| options | [IsolatedOptions](#isolatedoptions) | Yes | Constructor parameter to pass. Only valid on first input. Constructor parameter update is not supported. |

## IsolatedOptions

Used to pass construction parameters during **IsolatedComponent** construction.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type      | Read-Only| Optional| Description|
| ---- | ------------ | ---- | ---- | --------------- |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | No | No | The .abc file information to load. The .abc file runs in the restricted worker specified by the **worker** parameter. The parameters of the **Want** object must contain the following fields: **resourcePath** (resource path, which must be a .hap file path), **abcPath** (.abc file path verified by [verifyAbc](../../apis-ability-kit/js-apis-bundleManager-sys.md#bundlemanagerverifyabc11), which must start with '/abcs'), and **entryPoint** (.abc entry point, in the format of 'bundleName/page path'). |
| worker | [RestrictedWorker](../../apis-arkts/js-apis-worker-sys.md#restrictedworker11) | No | No | Restricted worker that runs the .abc file. Note that layout rendering and event delivery between the main thread and the restricted worker thread are asynchronous. |

## Attributes

Only the [width](ts-universal-attributes-size.md#width), [height](ts-universal-attributes-size.md#height), and [backgroundColor](ts-universal-attributes-background.md#backgroundcolor) universal attributes are supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

Events are asynchronously passed to the restricted Worker thread after coordinate conversion. Inter-thread event bubbling is not supported, and event conflicts may occur during inter-thread UI interactions.

The following events are supported:

### onError

onError(callback: ErrorCallback)

Invoked when an error occurs during the running of the .abc file loaded by **IsolatedComponent** (which runs as an Ability extension). You can obtain the error information based on the **code**, **name**, and **message** parameters in the callback and rectify the error accordingly.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                                  | Mandatory| Description          |
| --------------------- | ---------------------------------------------------------- | ---- | ------------------ |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes | Callback invoked when an error occurs. The error information including **code**, **name**, and **message** can be obtained through the callback parameters. |

## Example: Loading an IsolatedComponent

This example demonstrates the basic usage of the **IsolatedComponent** component. The sample application's **bundleName** is **"com.example.isolateddemo"**, and the component uses the .abc file and an extension page from the same application as the embedded content. The specific testing steps after building the application project are as follows:

1. Compile and build the HAP file in DevEco Studio and install it on the device.

2. Upload the generated **modules.abc** and **modules.hap** files to the app sandbox path **/data/app/el2/100/base/com.example.isolateddemo/haps/entry/files** using DevEco Studio or the [hdc tool](../../../dfx/hdc.md).

3. Open the app page and tap the **verifyAbc** button to verify the .abc file, which logs "VerifyAbc successfully."

4. After tapping the **showIsolatedComponent** button, the page displays the **IsolatedComponent** with the content "Hello World".

- The content of the restricted worker script **ets/workers/OhCardWorker.ets** is as follows:

  ```ts
  // OhCardWorker.ets
  import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

  const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

  workerPort.onmessage = (event: MessageEvents) => {
  };
  workerPort.onmessageerror = (event: MessageEvents) => {
  };
  workerPort.onerror = (event: ErrorEvent) => {
  };
  ```

- The content of the home page file **ets/pages/Index.ets** loaded by the **EntryAbility** (**UIAbility**) in the sample app is as follows:

  ```ts
  import { worker } from '@kit.ArkTS';
  import { bundleManager, common } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // Verify the .abc file and copy it to the specified sandbox path.
  function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean) {
    try {
      bundleManager.verifyAbc(abcPaths, deleteOriginalFiles, (err) => {
        if (err) {
          console.error(`VerifyAbc failed. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info("VerifyAbc successfully.");
        }
      });
    } catch (err) {
      let message = (err as BusinessError).message;
      console.error(`VerifyAbc failed. Code: ${(err as BusinessError).code}, message: ${message}`);
    }
  }

  @Entry
  @Component
  struct Index {
    @State isShow: boolean = false;
    @State resourcePath: string = "";
    @State abcPath: string = "";
    @State entryPoint: string = "";
    @State context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // .abc file name
    private fileName: string = "modules";
    // Bundle name of the application to which the .abc file belongs
    private bundleName: string = "com.example.isolateddemo";
    // Restricted Worker thread
    private worker?: worker.RestrictedWorker = new worker.RestrictedWorker("entry/ets/workers/OhCardWorker.ets");

    build() {
      Row() {
        Column() {
          // 1. Verify the .abc file.
          Button("verifyAbc").onClick(() => {
            let abcFilePath = `${this.context.filesDir}/${this.fileName}.abc`;
            console.info("abcFilePath: " + abcFilePath);
            verifyAbc([abcFilePath], false);
          }).height(100).width(100)

          // 2. Display the IsolatedComponent.
          Button("showIsolatedComponent").onClick(() => {
            if (!this.isShow) {
              // Resource path
              this.resourcePath = `${this.context.filesDir}/${this.fileName}.hap`;
              // Sandbox path after the .abc file is verified
              this.abcPath = `/abcs${this.context.filesDir}/${this.fileName}`;
              // Entry to the page to be displayed
              this.entryPoint = `${this.bundleName}/entry/ets/pages/extension`;
              this.isShow = true;
            }
          }).height(100).width(100)

          if (this.isShow) {
            IsolatedComponent({
              want: {
                "parameters": {
                  "resourcePath": this.resourcePath,
                  "abcPath": this.abcPath,
                  "entryPoint": this.entryPoint
                }
              },
              worker: this.worker
            })
              .width(300)
              .height(300)
              .onError((err) => {
                console.error(`IsolatedComponent onError. Code: ${err.code}, message: ${err.message}`);
              })
          }
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

- The entry page file **ets/pages/extension.ets**, which runs in a restricted Worker thread, needs to be configured in the **resources/base/profile/main_pages.json** file with the following content:

  ```ts
  @Entry
  @Component
  struct Extension {
    @State message: string = 'Hello World';

    build() {
      RelativeContainer() {
        Text(this.message)
          .id('HelloWorld')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .alignRules({
            center: { anchor: '__container__', align: VerticalAlign.Center },
            middle: { anchor: '__container__', align: HorizontalAlign.Center }
          })
      }
      .height('100%')
      .width('100%')
    }
  }
  ```

- Add the **requestPermissions** tag to the **module.json5** configuration file to allow the execution of dynamically delivered Ark bytecode in restricted mode.

  ```json
  "requestPermissions": [
    {
      "name": "ohos.permission.RUN_DYN_CODE",
      "usedScene": {
        "abilities": [
          "EntryAbility"
        ],
        "when": "inuse"
      }
    }
  ]
  ```