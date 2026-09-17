# @ohos.sendableResourceManager(Resource Manager)

This module provides the mutual conversion between [Resource](arkts-localization-sendableresourcemanager-resource-t.md) objects and [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) objects. `SendableResource` implements the [ISendable](../../../arkts-utils/arkts-sendable.md#isendable) API and supports cross-thread transmission. After cross-thread transmission, the `SendableResource` object can be converted back to a `Resource` object and passed as a parameter to the [resource management](arkts-localization-resourcemanager.md) APIs to obtain resources.

**Since:** 12

**System capability:** SystemCapability.Global.ResourceManager

## Modules to Import

```TypeScript
import { sendableResourceManager } from '@kit.LocalizationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [resourceToSendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md) | Converts a `Resource` object to a `SendableResource` object that can be used for cross-thread transmission. |
| [sendableResourceToResource](arkts-localization-sendableresourcemanager-sendableresourcetoresource-f.md) | Converts a `SendableResource` object transmitted across threads to a `Resource` object. |

### Types

| Name | Description |
| --- | --- |
| [Resource](arkts-localization-sendableresourcemanager-resource-t.md) | Represents resource-related information, including the application bundle name, application module name, resource ID, resource type, and other resource parameters. |
| [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) | Represents Sendable resource-related information for cross-thread transmission, including the application bundle name, application module name, resource ID, resource type, and other resource parameters. |
