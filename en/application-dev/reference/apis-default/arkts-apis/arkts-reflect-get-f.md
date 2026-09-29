# get

## Modules to Import

```TypeScript
```

## get

```TypeScript
function get<T extends object, P extends PropertyKey>(
        target: T,
        propertyKey: P,
        receiver?: unknown,
    ): P extends keyof T ? T[P] : any
```

Gets the property of target, equivalent to `target[propertyKey]` when `receiver === target`.

<!--Device-Reflect-function get<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,        receiver?: unknown,    ): P extends keyof T ? T[P] : any--><!--Device-Reflect-function get<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,        receiver?: unknown,    ): P extends keyof T ? T[P] : any-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| propertyKey | P | Yes |  |
| receiver | unknown | No |  |
