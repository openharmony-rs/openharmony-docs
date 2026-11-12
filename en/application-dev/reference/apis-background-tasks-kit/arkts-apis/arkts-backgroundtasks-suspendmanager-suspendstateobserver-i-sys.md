# SuspendStateObserver (System API)

```TypeScript
export interface SuspendStateObserver
```

Defines the observer for suspend state changes.

**Since:** 26.1.0

<!--Device-suspendManager-export interface SuspendStateObserver--><!--Device-suspendManager-export interface SuspendStateObserver-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## onActive

```TypeScript
onActive(pidList: Array<number>, uid: number): void
```

Called when the application transitions to the active state.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SuspendStateObserver-onActive(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onActive(pidList: Array<int>, uid: int): void-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | Yes | List of PIDs that transitioned to the active state. |
| uid | number | Yes | UID of the application. <br>The value should be an integer. |

## onDoze

```TypeScript
onDoze(pidList: Array<number>, uid: number): void
```

Called when the application enters the doze state.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SuspendStateObserver-onDoze(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onDoze(pidList: Array<int>, uid: int): void-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | Yes | List of PIDs that transitioned to the doze state. |
| uid | number | Yes | UID of the application. <br>The value should be an integer. |

## onFrozen

```TypeScript
onFrozen(pidList: Array<number>, uid: number): void
```

Called when the application is fully frozen.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SuspendStateObserver-onFrozen(pidList: Array<int>, uid: int): void--><!--Device-SuspendStateObserver-onFrozen(pidList: Array<int>, uid: int): void-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | Yes | List of PIDs that transitioned to the frozen state. |
| uid | number | Yes | UID of the application. <br>The value should be an integer. |
