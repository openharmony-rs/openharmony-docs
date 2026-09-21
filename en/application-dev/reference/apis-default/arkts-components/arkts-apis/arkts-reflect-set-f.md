# set

## Modules to Import

```TypeScript
```

## set

```TypeScript
function set<T extends object, P extends PropertyKey>(
        target: T,
        propertyKey: P,
        value: P extends keyof T ? T[P] : any,
        receiver?: any,
    ): boolean
```

Sets the property of target, equivalent to `target[propertyKey] = value` when `receiver === target`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| propertyKey | P | Yes |  |
| value | P extends keyof T ? T[P] : any | Yes |  |
| receiver | any | No |  |


<a id="set-1"></a>

## set

```TypeScript
function set(target: object, propertyKey: PropertyKey, value: any, receiver?: any): boolean
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | object | Yes |  |
| propertyKey | [PropertyKey](arkts-propertykey-t.md) | Yes |  |
| value | any | Yes |  |
| receiver | any | No |  |
