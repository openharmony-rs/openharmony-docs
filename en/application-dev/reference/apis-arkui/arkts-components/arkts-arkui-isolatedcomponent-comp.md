# IsolatedComponent(System API)

**IsolatedComponent** is designed to support the embedding and display of UIs provided by independent .abc files (Ark bytecode) within the current page, with the displayed content running in a restricted Worker thread.

This component is primarily designed for modular development scenarios that require hot updates for .abc files. (The .abc files loaded by **IsolatedComponent** can be dynamically replaced, enabling content updates without reinstalling the app.)

## Child Components

Not supported

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [IsolatedOptions](arkts-arkui-isolatedcomponent-comp-isolatedoptions-i-sys.md) | Used to pass construction parameters during **IsolatedComponent** construction. |

### Types

| Name | Description |
| --- | --- |
| [ErrorCallback](arkts-arkui-isolatedcomponent-comp-errorcallback-t-sys.md) | Indicates error callback. |
| [RestrictedWorker](arkts-arkui-isolatedcomponent-comp-restrictedworker-t-sys.md) | Restricted worker that runs the .abc file. |
| [Want](arkts-arkui-isolatedcomponent-comp-want-t-sys.md) | Indicates want. |
