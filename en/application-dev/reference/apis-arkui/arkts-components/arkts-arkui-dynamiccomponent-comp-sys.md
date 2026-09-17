# DynamicComponent(System API) (System API)

**DynamicComponent** is designed to support the embedding and display of UIs provided by independent .abc files within the current page, with the displayed content running in a worker thread.

It is typically used in modular development scenarios where .abc pages are dynamically loaded.

## Child Components

None

## DynamicComponent

```TypeScript
DynamicComponent(options: DynamicOptions)
```

Creates a **DynamicComponent** component to display the .abc UI running in the worker thread.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DynamicOptions](arkts-arkui-dynamicoptions-i-sys.md) | Yes | Configuration parameters for constructing a **DynamicComponent**, which are used to configure the entry of the .abc page to be loaded, worker thread to run, and display options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DynamicOptions](arkts-arkui-dynamicoptions-i-sys.md) | Defines the parameters to be passed during **DynamicComponent** construction. |

### Types

| Name | Description |
| --- | --- |
| [ErrorCallback](arkts-arkui-errorcallback-t-sys.md) | Defines the error callback type, which is used to receive exception information. |
| [Worker](arkts-arkui-worker-t-sys.md) | Defines the worker thread object for running the .abc file. |
