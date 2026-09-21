# CameraCaptureStateChangeInfo

```TypeScript
declare interface CameraCaptureStateChangeInfo
```

Provides the state change information of the camera when the callback is triggered, including the state before the change and the new state. It is suitable for scenarios where monitoring camera state changes is required, improving camera management visibility and user experience.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## newState

```TypeScript
newState: CameraCaptureState
```

New state.

**Type:** [CameraCaptureState](arkts-arkweb-web-comp-cameracapturestate-e.md)

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## originalState

```TypeScript
originalState: CameraCaptureState
```

State before the change.

**Type:** [CameraCaptureState](arkts-arkweb-web-comp-cameracapturestate-e.md)

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core
