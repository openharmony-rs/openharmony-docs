# LaunchAtomicServiceCallback (System API)

```TypeScript
export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void
```

Triggered when an atomic service is launched.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | App ID for the atomic service. |
| options | [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) | No | Parameters for launching the atomic service. |
