# ProxyHandler

```TypeScript
interface ProxyHandler<T extends object>
```

## Modules to Import

```TypeScript
```

## apply

```TypeScript
apply?(target: T, thisArg: any, argArray: any[]): any
```

A trap method for a function call.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| thisArg | any | Yes |  |
| argArray | any[] | Yes |  |

## construct

```TypeScript
construct?(target: T, argArray: any[], newTarget: Function): object
```

A trap for the `new` operator.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| argArray | any[] | Yes |  |
| newTarget | Function | Yes |  |

## defineProperty

```TypeScript
defineProperty?(target: T, property: string | symbol, attributes: PropertyDescriptor): boolean
```

A trap for `Object.defineProperty()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| property | string &#124; symbol | Yes |  |
| attributes | PropertyDescriptor | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | A `Boolean` indicating whether or not the property has been defined. |

## deleteProperty

```TypeScript
deleteProperty?(target: T, p: string | symbol): boolean
```

A trap for the `delete` operator.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| p | string &#124; symbol | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | A `Boolean` indicating whether or not the property was deleted. |

## get

```TypeScript
get?(target: T, p: string | symbol, receiver: any): any
```

A trap for getting a property value.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| p | string &#124; symbol | Yes |  |
| receiver | any | Yes |  |

## getOwnPropertyDescriptor

```TypeScript
getOwnPropertyDescriptor?(target: T, p: string | symbol): PropertyDescriptor | undefined
```

A trap for `Object.getOwnPropertyDescriptor()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| p | string &#124; symbol | Yes |  |

## getPrototypeOf

```TypeScript
getPrototypeOf?(target: T): object | null
```

A trap for the `[[GetPrototypeOf]]` internal method.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## has

```TypeScript
has?(target: T, p: string | symbol): boolean
```

A trap for the `in` operator.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| p | string &#124; symbol | Yes |  |

## isExtensible

```TypeScript
isExtensible?(target: T): boolean
```

A trap for `Object.isExtensible()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## ownKeys

```TypeScript
ownKeys?(target: T): ArrayLike<string | symbol>
```

A trap for `Reflect.ownKeys()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## preventExtensions

```TypeScript
preventExtensions?(target: T): boolean
```

A trap for `Object.preventExtensions()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## set

```TypeScript
set?(target: T, p: string | symbol, newValue: any, receiver: any): boolean
```

A trap for setting a property value.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| p | string &#124; symbol | Yes |  |
| newValue | any | Yes |  |
| receiver | any | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | A `Boolean` indicating whether or not the property was set. |

## setPrototypeOf

```TypeScript
setPrototypeOf?(target: T, v: object | null): boolean
```

A trap for `Object.setPrototypeOf()`.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| v | object &#124; null | Yes |  |
