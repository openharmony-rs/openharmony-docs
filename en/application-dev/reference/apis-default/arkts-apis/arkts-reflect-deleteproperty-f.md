# deleteProperty

## Modules to Import

```TypeScript
```

## deleteProperty

```TypeScript
function deleteProperty(target: object, propertyKey: PropertyKey): boolean
```

Removes a property from an object, equivalent to `delete target[propertyKey]`, except it won't throw if `target[propertyKey]` is non-configurable.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | object | Yes |  |
| propertyKey | [PropertyKey](arkts-propertykey-t.md) | Yes |  |
