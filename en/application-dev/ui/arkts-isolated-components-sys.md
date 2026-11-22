# Cross-Thread Embedded Component (IsolatedComponent, for System Applications Only)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=929cb053abb8e1835779a4783f90dad90a9d7bf4 translatedAt=2026-11-03T08:33:07.109Z pushedAt=2026-11-03T09:15:42.109Z nl=1 -->

**IsolatedComponent** is a cross-thread embedded component that can embed and display isolated UI content provided by an independent .abc file within the current page. This content runs independently in a restricted worker thread without interfering with each other.

Each **IsolatedComponent** exists independently with its own scope and lifecycle, not sharing state or data with other components. This facilitates reuse across applications, reducing repetitive development efforts.

## Basic Concepts

[IsolatedComponent](../reference/apis-arkui/arkui-ts/ts-container-isolated-component-sys.md) is designed to embed and display a UI provided by an independent .abc file within the current page, with its content executed in a restricted [worker](../reference/apis-arkts/js-apis-worker-sys.md#restrictedworker11) thread.

This component is typically used in modular development scenarios that require hot updates for .abc files (where the .abc file loaded by **IsolatedComponent** can be dynamically replaced, enabling content updates without reinstalling the app).

## Constraints

1. The .abc file must pass [VerifyAbc](../reference/apis-ability-kit/js-apis-bundleManager-sys.md#bundlemanagerverifyabc11) verification before use.

2. Constructor parameter updates are not supported; only the initial input is effective.

3. Nesting of **IsolatedComponent** components is not supported.

4. The main thread and the restricted Worker thread handle layout rendering asynchronously, which can lead to desynchronization in page changes caused by layout alterations or rotations.

5. Event passing between the main thread and the restricted Worker thread is managed asynchronously, and there is no support for event bubbling between threads. As a result, UI interactions between threads may encounter event conflicts.

6. When an independent .abc file is embedded into the host process using the **IsolatedComponent**, its content is fully open to the host, which can operate on the content. Therefore, this feature should be disabled in security-sensitive scenarios.

7. The independent .abc file runs in a restricted worker thread, which ensures relative security and prevents main thread crashes or direct impact on the data integrity of the main thread.

## Scenario Example

This example demonstrates the basic usage of the **IsolatedComponent** component. The sample application's **bundleName** is **"com.example.isolateddemo"**, and the component uses the .abc file and an extension page from the same application as the embedded content.

**Importing the Core Module**

When using the **IsolatedComponent**, you need to import the @kit.AbilityKit and @kit.ArkTS modules:

- @kit.AbilityKit provides key application package management APIs such as bundleManager, which are used to validate .abc files.
- @kit.ArkTS provides the restricted worker (RestrictedWorker) capability, which is used to run isolated UI content.

bundleManager is a module in @kit.AbilityKit that provides application package management capabilities. By importing this module, you can use its verifyAbc API to validate .abc files. This is a necessary step before using the **IsolatedComponent** and provides a prerequisite guarantee for the secure loading of .abc content by the **IsolatedComponent**.

```ts
import { bundleManager } from '@kit.AbilityKit';
import { worker } from '@kit.ArkTS';
```

**Managing Permissions**

When using the **IsolatedComponent**, properly configure the [requestPermissions](../security/AccessToken/declare-permissions.md) tag, which is crucial for ensuring the secure operation of components in restricted environments. This configuration allows you to specify the permissions required by the component, enabling fine-grained permission management.

In restricted mode, the **IsolatedComponent** does not have the ability to execute dynamic code by default. By adding the **requestPermissions** tag in the **module.json5** configuration file to declare the required permissions, the component can gain the ability to execute dynamically delivered ArkCompiler bytecode under specific conditions.

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

**Restricted Worker**

A restricted [worker](../reference/apis-arkts/js-apis-worker-sys.md#restrictedworker11) is a worker thread that runs in an isolated environment. This isolation ensures memory isolation between the restricted worker and other threads or components, preventing mutual interference or security issues.

In the **IsolatedComponent** scenario, the component often needs to dynamically load external HAP resources. The restricted worker ensures security through the following mechanisms:

- [Sandbox path](../file-management/app-sandbox-directory.md) validation

  **abcPath** points to an .abc file in a system-verified secure directory, preventing malicious code injection.

- Communication control

  Only standardized message events are allowed for communication between the main thread and the Worker thread, with direct data sharing prohibited.

- Exception isolation

  Errors within the worker do not cause the main app to crash and can be handled in a controlled manner through the [onerror](../reference/apis-arkts/js-apis-worker.md#properties) event.

```ts
// OhCardWorker.ets
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {}
workerPort.onmessageerror = (e: MessageEvents) => {}
workerPort.onerror = (e: ErrorEvent) => {}
```
<!--deprecated_code_no_check-->
```ts
IsolatedComponent({
  want: {
    "parameters": {
      // Resource path
      "resourcePath": `${this.getUIContext().getHostContext()?.filesDir}/${this.fileName}.hap`,
      // Verified sandbox path for the .abc file
      "abcPath": `/abcs${this.getUIContext().getHostContext()?.filesDir}/${this.fileName}`,
      // Entry path for the page to be displayed
      "entryPoint": `${this.bundleName}/entry/ets/pages/extension`,
    }
  },
  // Restricted Worker thread
  worker: new worker.RestrictedWorker("entry/ets/workers/OhCardWorker.ets")
})
```

The **IsolatedComponent** achieves dynamic component loading and isolated execution through the **want** and **worker** constructor parameters, which together form the security boundary. Properly setting these constructor parameters is key to ensuring the secure operation of the component.

Among them, the entry page file ets/pages/extension.ets, which runs in the restricted worker thread, requires the page path to be configured in the resources/base/profile/main_pages.json file. The content of this page file is as follows:

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

**Sample Application Code**

The following example shows the content of the home page file **ets/pages/Index.ets** loaded by EntryAbility (UIAbility) in the application.

```ts
import { worker } from '@kit.ArkTS';
import { bundleManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Verify the .abc file and copy it to the specified sandbox path.
function VerifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean) {
  try {
    bundleManager.verifyAbc(abcPaths, deleteOriginalFiles, (err) => {
      if (err) {
        console.error("VerifyAbc failed, error message: " + err.message);
      } else {
        console.info("VerifyAbc successfully.");
      }
    });
  } catch (err) {
    let message = (err as BusinessError).message;
    console.error("VerifyAbc failed, error message: " + message);
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
  private worker ?: worker.RestrictedWorker = new worker.RestrictedWorker("entry/ets/workers/OhCardWorker.ets");

  build() {
    Row() {
      Column({ space: 20 }) {
        // 1. Verify the .abc file.
        Button("verifyAbc").onClick(() => {
          let abcFilePath = `${this.context.filesDir}/${this.fileName}.abc`;
          console.info("abcFilePath: " + abcFilePath);
          VerifyAbc([abcFilePath], false);
        }).height(100).width(200)

        // 2. Display the IsolatedComponent.
        Button("showIsolatedComponent").onClick(() => {
          if (!this.isShow) {
            // Resource path
            this.resourcePath = `${this.context.filesDir}/${this.fileName}.hap`;
            // Verified sandbox path for the .abc file
            this.abcPath = `/abcs${this.context.filesDir}/${this.fileName}`;
            // Entry path for the page to be displayed
            this.entryPoint = `${this.bundleName}/entry/ets/pages/extension`;
            this.isShow = true;
          }
        }).height(100).width(200)

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
              console.error("onError : " + JSON.stringify(err));
            })
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

**Expected Results**

1. Compile and build the HAP package in DevEco Studio, and install it on the device.

2. Upload the **modules.abc** file generated by the application to the application sandbox path **/data/app/el2/100/base/com.example.isolateddemo/haps/entry/files** using DevEco Studio or the hdc tool. The reference command for the hdc tool is as follows:

   ```bash
   hdc file send modules.abc /data/app/el2/100/base/com.example.isolateddemo/haps/entry/files/
   ```

3. Open the application page and click the **verifyAbc** button to verify the .abc file. The log "VerifyAbc successfully." should be output;

   ![en-us_image_0000001746521386](figures/verifyAbc.jpg)

   ![en-us_image_0000001502381065](figures/VerifyAbc-successfully.png)

4. Click the **showIsolatedComponent** button to display the **IsolatedComponent** with the content "Hello World."
