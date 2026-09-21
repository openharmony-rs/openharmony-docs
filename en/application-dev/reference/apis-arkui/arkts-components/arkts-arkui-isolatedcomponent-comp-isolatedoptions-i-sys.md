# IsolatedOptions (System API)

```TypeScript
declare interface IsolatedOptions
```

Describes the optional construction parameters during **IsolatedComponent** construction.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

.abc file information to load.

**Type:** [Want](arkts-arkui-isolatedcomponent-comp-want-t-sys.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## worker

```TypeScript
worker: RestrictedWorker
```

Restricted Worker thread where the .abc file is running.

**Type:** [RestrictedWorker](arkts-arkui-isolatedcomponent-comp-restrictedworker-t-sys.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
