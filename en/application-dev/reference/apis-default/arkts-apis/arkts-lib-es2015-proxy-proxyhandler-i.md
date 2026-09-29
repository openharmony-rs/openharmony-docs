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

<!--Device-ProxyHandler-apply?(target: T, thisArg: any, argArray: any[]): any--><!--Device-ProxyHandler-apply?(target: T, thisArg: any, argArray: any[]): any-End-->

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

<!--Device-ProxyHandler-construct?(target: T, argArray: any[], newTarget: Function): object--><!--Device-ProxyHandler-construct?(target: T, argArray: any[], newTarget: Function): object-End-->

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

<!--Device-ProxyHandler-defineProperty?(target: T, property: string | symbol, attributes: PropertyDescriptor): boolean--><!--Device-ProxyHandler-defineProperty?(target: T, property: string | symbol, attributes: PropertyDescriptor): boolean-End-->

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

<!--Device-ProxyHandler-deleteProperty?(target: T, p: string | symbol): boolean--><!--Device-ProxyHandler-deleteProperty?(target: T, p: string | symbol): boolean-End-->

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

<!--Device-ProxyHandler-get?(target: T, p: string | symbol, receiver: any): any--><!--Device-ProxyHandler-get?(target: T, p: string | symbol, receiver: any): any-End-->

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

<!--Device-ProxyHandler-getOwnPropertyDescriptor?(target: T, p: string | symbol): PropertyDescriptor | undefined--><!--Device-ProxyHandler-getOwnPropertyDescriptor?(target: T, p: string | symbol): PropertyDescriptor | undefined-End-->

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

<!--Device-ProxyHandler-getPrototypeOf?(target: T): object | null--><!--Device-ProxyHandler-getPrototypeOf?(target: T): object | null-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## has

```TypeScript
has?(target: T, p: string | symbol): boolean
```

A trap for the `in` operator.

<!--Device-ProxyHandler-has?(target: T, p: string | symbol): boolean--><!--Device-ProxyHandler-has?(target: T, p: string | symbol): boolean-End-->

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

<!--Device-ProxyHandler-isExtensible?(target: T): boolean--><!--Device-ProxyHandler-isExtensible?(target: T): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## ownKeys

```TypeScript
ownKeys?(target: T): ArrayLike<string | symbol>
```

A trap for `Reflect.ownKeys()`.

<!--Device-ProxyHandler-ownKeys?(target: T): ArrayLike<string | symbol>--><!--Device-ProxyHandler-ownKeys?(target: T): ArrayLike<string | symbol>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## preventExtensions

```TypeScript
preventExtensions?(target: T): boolean
```

A trap for `Object.preventExtensions()`.

<!--Device-ProxyHandler-preventExtensions?(target: T): boolean--><!--Device-ProxyHandler-preventExtensions?(target: T): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |

## set

```TypeScript
set?(target: T, p: string | symbol, newValue: any, receiver: any): boolean
```

A trap for setting a property value.

<!--Device-ProxyHandler-set?(target: T, p: string | symbol, newValue: any, receiver: any): boolean--><!--Device-ProxyHandler-set?(target: T, p: string | symbol, newValue: any, receiver: any): boolean-End-->

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

<!--Device-ProxyHandler-setPrototypeOf?(target: T, v: object | null): boolean--><!--Device-ProxyHandler-setPrototypeOf?(target: T, v: object | null): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| v | object &#124; null | Yes |  |
