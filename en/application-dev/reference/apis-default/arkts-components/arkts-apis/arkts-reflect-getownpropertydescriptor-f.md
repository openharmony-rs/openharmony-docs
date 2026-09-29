# getOwnPropertyDescriptor

## Modules to Import

```TypeScript
```

## getOwnPropertyDescriptor

```TypeScript
function getOwnPropertyDescriptor<T extends object, P extends PropertyKey>(
        target: T,
        propertyKey: P,
    ): TypedPropertyDescriptor<P extends keyof T ? T[P] : any> | undefined
```

Gets the own property descriptor of the specified object. An own property descriptor is one that is defined directly on the object and is not inherited from the object's prototype.

<!--Device-Reflect-function getOwnPropertyDescriptor<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,    ): TypedPropertyDescriptor<P extends keyof T ? T[P] : any> | undefined--><!--Device-Reflect-function getOwnPropertyDescriptor<T extends object, P extends PropertyKey>(        target: T,        propertyKey: P,    ): TypedPropertyDescriptor<P extends keyof T ? T[P] : any> | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| propertyKey | P | Yes |  |
