# IsolatedOptions (System API)

```TypeScript
declare interface IsolatedOptions
```

Used to pass construction parameters during **IsolatedComponent** construction.

**Since:** 12

<!--Device-unnamed-declare interface IsolatedOptions--><!--Device-unnamed-declare interface IsolatedOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

The .abc file information to load. The .abc file runs in the restricted worker specified by the **worker** parameter. The parameters of the **Want** object must contain the following fields: **resourcePath** (resource path, which must be a .hap file path), **abcPath** (.abc file path verified by [verifyAbc](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-verifyabc-f-sys.md), which must start with '/abcs'), and **entryPoint** (.abc entry point, in the format of 'bundleName/page path').

**Type:** [Want](arkts-arkui-isolatedcomponent-comp-want-t-sys.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IsolatedOptions-want: Want--><!--Device-IsolatedOptions-want: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## worker

```TypeScript
worker: RestrictedWorker
```

Restricted worker that runs the .abc file. Note that layout rendering and event delivery between the main thread and the restricted worker thread are asynchronous.

**Type:** [RestrictedWorker](arkts-arkui-isolatedcomponent-comp-restrictedworker-t-sys.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IsolatedOptions-worker: RestrictedWorker--><!--Device-IsolatedOptions-worker: RestrictedWorker-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
