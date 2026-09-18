# OnLoadInterceptCallback

```TypeScript
export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean
```

Represents the callback invoked when resource loading is intercepted.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnLoadInterceptEvent](arkts-arkui-atomicservice-atomicserviceweb-onloadinterceptevent-i.md) | Yes | Event triggered when resource loading is intercepted. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether resource loading is intercepted. The value **true** indicates that resource loading is intercepted. |
