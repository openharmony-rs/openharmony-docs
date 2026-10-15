# PluginComponent(System API) (System API)

Provides the embedded display capability for external application components, that is, the UI provided by an external application can be displayed within this application. It applies to scenarios where UI components need to be reused across applications, such as embedding pages or cards of other applications to implement UI collaboration and data interaction between applications. To implement updates through inter-process communication (IPC), see [@ohos.pluginComponent](../arkts-apis/arkts-arkui-plugincomponentmanager-n.md).

## Child Components

Not supported

## PluginComponent

```TypeScript
PluginComponent(options: PluginComponentOptions)
```

Creates a **PluginComponent** to display the UI provided by an external application.

**Since:** 9

<!--Device-PluginComponentInterface-(options: PluginComponentOptions): PluginComponentAttribute--><!--Device-PluginComponentInterface-(options: PluginComponentOptions): PluginComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PluginComponentOptions](arkts-arkui-plugincomponent-comp-plugincomponentoptions-i-sys.md) | Yes | Configuration options of the **PluginComponent**. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PluginComponentOptions](arkts-arkui-plugincomponent-comp-plugincomponentoptions-i-sys.md) | Defines options for constructing a **PluginComponent**. |
| [PluginComponentTemplate](arkts-arkui-plugincomponent-comp-plugincomponenttemplate-i-sys.md) | Defines the plugin component template information, which is used to bind to the component defined by the provider. |
| [PluginErrorData](arkts-arkui-plugincomponent-comp-pluginerrordata-i-sys.md) | Data provided when the error occurs. |

### Types

| Name | Description |
| --- | --- |
| [PluginErrorCallback](arkts-arkui-plugincomponent-comp-pluginerrorcallback-t-sys.md) | Callback invoked when an error occurs. |
