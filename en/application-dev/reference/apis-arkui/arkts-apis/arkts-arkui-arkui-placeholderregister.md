# @ohos.arkui.placeholderRegister

## Modules to Import

```TypeScript
import { PlaceholderOptions, PlaceholderProvider, PlaceholderRegister } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PlaceholderRegister](arkts-arkui-arkui-placeholderregister-placeholderregister-c.md) | Provides the methods for registering, unregistering, and querying scroll placeholder builders. Each UI instance holds its own registry: builders registered in one instance are not visible to another. Do not create instances of this class; use [getPlaceholderRegister()](arkts-arkui-arkui-uicontext-uicontext-c.md#getplaceholderregister) to obtain the registry of the current UI instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [PlaceholderOptions](arkts-arkui-arkui-placeholderregister-placeholderoptions-i.md) | Describes the placeholder to display for an item of a scrollable component while the real item is being created across frames. |

### Types

| Name | Description |
| --- | --- |
| [PlaceholderProvider](arkts-arkui-placeholderprovider-t.md) | Provides the placeholder description for an item of a scrollable component. |
