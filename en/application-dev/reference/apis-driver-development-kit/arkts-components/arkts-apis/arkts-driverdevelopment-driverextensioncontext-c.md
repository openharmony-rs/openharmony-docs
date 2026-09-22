# DriverExtensionContext

```TypeScript
declare class DriverExtensionContext extends ExtensionContext
```

The **DriverExtensionContext** module provides the context of **DriverExtensionAbility**. It inherits from **ExtensionContext**. The **DriverExtensionContext** module provides the operations that need to be actively initiated in the **DriverExtensionAbility** implementation.

> **NOTE:** 
> - The APIs of this module can be used only in the stage model.

**Inheritance/Implementation:** DriverExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 10

**System capability:** SystemCapability.Driver.ExternalDevice

## updateDriverState

```TypeScript
updateDriverState(): void
```

Updates the driver state. This interface is reserved and does not provide specific functionality currently.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Driver.ExternalDevice

**Examples**

```TypeScript
// The current code implementation depends on the code implementation in the previous section.
if (context != null) {
  context.updateDriverState();
}
```
