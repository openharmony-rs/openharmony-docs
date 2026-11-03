# DriverExtensionContext(Driver Extension Context)

## How to Use

Before using **DriverExtensionContext**, you need to obtain it through a **DriverExtensionAbility** child class instance.

```ts
 let context: DriverExtensionContext | undefined;
 class EntryAbility extends DriverExtensionAbility {
 onInit() {
 context = this.context; // Obtain DriverExtensionContext.
 }
 }
 ```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [DriverExtensionContext](arkts-driverdevelopment-driverextensioncontext-c.md) | The **DriverExtensionContext** module provides the context of **DriverExtensionAbility**. It inherits from **ExtensionContext**. |
