# PluginComponent(System API) (System API)

The **PluginComponent** allows an application to display external UI from another application. To implement update through inter-process communication (IPC), see [@ohos.pluginComponent](../arkts-apis/arkts-arkui-plugincomponentmanager-n.md).

## Child Components

Not supported

## PluginComponent

```TypeScript
PluginComponent(options: PluginComponentOptions)
```

Creates a **PluginComponent** to display the UI provided by an external application.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PluginComponentOptions](arkts-arkui-plugincomponentoptions-i-sys.md) | Yes | Configuration options of the **PluginComponent**. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PluginComponentOptions](arkts-arkui-plugincomponentoptions-i-sys.md) | Defines options for constructing a **PluginComponent**. |
| [PluginComponentTemplate](arkts-arkui-plugincomponenttemplate-i-sys.md) | [PluginComponentTemplate](arkts-arkui-plugincomponenttemplate-i-sys.md) |
| [PluginErrorData](arkts-arkui-pluginerrordata-i-sys.md) | Data provided when the error occurs. |

### Types

| Name | Description |
| --- | --- |
| [PluginErrorCallback](arkts-arkui-pluginerrorcallback-t-sys.md) | Callback invoked when an error occurs. |
