# set

## Modules to Import

```TypeScript
```

<a id="set1"></a>

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

<!--Device-Reflect-function set<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,        value: P extends keyof T ? T[P] : any,        receiver?: any,    ): boolean--><!--Device-Reflect-function set<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,        value: P extends keyof T ? T[P] : any,        receiver?: any,    ): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| propertyKey | P | Yes |  |
| value | P extends keyof T ? T[P] : any | Yes |  |
| receiver | any | No |  |


<a id="set2"></a>

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
