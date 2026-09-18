# TypeDecorator

```TypeScript
export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator
```

Defines the attribute decorator, which is used to decorate attributes of the custom class in a nested class.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md)&lt;T&gt; | Yes | Type of the class property. |

**Return value:**

| Type | Description |
| --- | --- |
| [PropertyDecorator](../../apis-default/arkts-apis/arkts-propertydecorator-t.md) | Property decorator. |
