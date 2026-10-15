# ObjectConstructor

```TypeScript
interface ObjectConstructor
```

## Modules to Import

```TypeScript
```

<a id="call1"></a>

## [[Call]]

```TypeScript
(): any
```

<a id="call2"></a>

## [[Call]]

```TypeScript
(value: any): any
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | any | Yes |  |

## [[Construct]]

```TypeScript
new(value?: any): Object
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | any | No |  |

<a id="create1"></a>

## create

```TypeScript
create(o: object | null): any
```

Creates an object that has the specified prototype or that has null prototype.

<!--Device-ObjectConstructor-create(o: object | null): any--><!--Device-ObjectConstructor-create(o: object | null): any-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | object &#124; null | Yes |  |

<a id="create2"></a>

## create

```TypeScript
create(o: object | null, properties: PropertyDescriptorMap & ThisType<any>): any
```

Creates an object that has the specified prototype, and that optionally contains specified properties.

<!--Device-ObjectConstructor-create(o: object | null, properties: PropertyDescriptorMap & ThisType<any>): any--><!--Device-ObjectConstructor-create(o: object | null, properties: PropertyDescriptorMap & ThisType<any>): any-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | object &#124; null | Yes |  |
| properties | PropertyDescriptorMap & ThisType&lt;any&gt; | Yes |  |

## defineProperties

```TypeScript
defineProperties<T>(o: T, properties: PropertyDescriptorMap & ThisType<any>): T
```

Adds one or more properties to an object, and/or modifies attributes of existing properties.

<!--Device-ObjectConstructor-defineProperties<T>(o: T, properties: PropertyDescriptorMap & ThisType<any>): T--><!--Device-ObjectConstructor-defineProperties<T>(o: T, properties: PropertyDescriptorMap & ThisType<any>): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |
| properties | PropertyDescriptorMap & ThisType&lt;any&gt; | Yes |  |

## defineProperty

```TypeScript
defineProperty<T>(o: T, p: PropertyKey, attributes: PropertyDescriptor & ThisType<any>): T
```

Adds a property to an object, or modifies attributes of an existing property.

<!--Device-ObjectConstructor-defineProperty<T>(o: T, p: PropertyKey, attributes: PropertyDescriptor & ThisType<any>): T--><!--Device-ObjectConstructor-defineProperty<T>(o: T, p: PropertyKey, attributes: PropertyDescriptor & ThisType<any>): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |
| p | [PropertyKey](arkts-propertykey-t.md) | Yes |  |
| attributes | PropertyDescriptor & ThisType&lt;any&gt; | Yes |  |

<a id="freeze1"></a>

## freeze

```TypeScript
freeze<T extends Function>(f: T): T
```

Prevents the modification of existing property attributes and values, and prevents the addition of new properties.

<!--Device-ObjectConstructor-freeze<T extends Function>(f: T): T--><!--Device-ObjectConstructor-freeze<T extends Function>(f: T): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| f | T | Yes |  |

<a id="freeze2"></a>

## freeze

```TypeScript
freeze<T extends {[idx: string]: U | null | undefined | object}, U extends string | bigint | number | boolean | symbol>(o: T): Readonly<T>
```

Prevents the modification of existing property attributes and values, and prevents the addition of new properties.

<!--Device-ObjectConstructor-freeze<T extends {[idx: string]: U | null | undefined | object}, U extends string | bigint | number | boolean | symbol>(o: T): Readonly<T>--><!--Device-ObjectConstructor-freeze<T extends {[idx: string]: U | null | undefined | object}, U extends string | bigint | number | boolean | symbol>(o: T): Readonly<T>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |

<a id="freeze3"></a>

## freeze

```TypeScript
freeze<T>(o: T): Readonly<T>
```

Prevents the modification of existing property attributes and values, and prevents the addition of new properties.

<!--Device-ObjectConstructor-freeze<T>(o: T): Readonly<T>--><!--Device-ObjectConstructor-freeze<T>(o: T): Readonly<T>-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |

## getOwnPropertyDescriptor

```TypeScript
getOwnPropertyDescriptor(o: any, p: PropertyKey): PropertyDescriptor | undefined
```

Gets the own property descriptor of the specified object. An own property descriptor is one that is defined directly on the object and is not inherited from the object's prototype.

<!--Device-ObjectConstructor-getOwnPropertyDescriptor(o: any, p: PropertyKey): PropertyDescriptor | undefined--><!--Device-ObjectConstructor-getOwnPropertyDescriptor(o: any, p: PropertyKey): PropertyDescriptor | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |
| p | [PropertyKey](arkts-propertykey-t.md) | Yes |  |

## getOwnPropertyNames

```TypeScript
getOwnPropertyNames(o: any): string[]
```

Returns the names of the own properties of an object. The own properties of an object are those that are defined directly on that object, and are not inherited from the object's prototype. The properties of an object include both fields (objects) and functions.

<!--Device-ObjectConstructor-getOwnPropertyNames(o: any): string[]--><!--Device-ObjectConstructor-getOwnPropertyNames(o: any): string[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |

## getPrototypeOf

```TypeScript
getPrototypeOf(o: any): any
```

Returns the prototype of an object.

<!--Device-ObjectConstructor-getPrototypeOf(o: any): any--><!--Device-ObjectConstructor-getPrototypeOf(o: any): any-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |

## isExtensible

```TypeScript
isExtensible(o: any): boolean
```

Returns a value that indicates whether new properties can be added to an object.

<!--Device-ObjectConstructor-isExtensible(o: any): boolean--><!--Device-ObjectConstructor-isExtensible(o: any): boolean-End-->

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |

## isFrozen

```TypeScript
isFrozen(o: any): boolean
```

Returns true if existing property attributes and values cannot be modified in an object, and new properties cannot be added to the object.

<!--Device-ObjectConstructor-isFrozen(o: any): boolean--><!--Device-ObjectConstructor-isFrozen(o: any): boolean-End-->

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |

## isSealed

```TypeScript
isSealed(o: any): boolean
```

Returns true if existing property attributes cannot be modified in an object and new properties cannot be added to the object.

<!--Device-ObjectConstructor-isSealed(o: any): boolean--><!--Device-ObjectConstructor-isSealed(o: any): boolean-End-->

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | any | Yes |  |

## keys

```TypeScript
keys(o: object): string[]
```

Returns the names of the enumerable string properties and methods of an object.

<!--Device-ObjectConstructor-keys(o: object): string[]--><!--Device-ObjectConstructor-keys(o: object): string[]-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | object | Yes |  |

## preventExtensions

```TypeScript
preventExtensions<T>(o: T): T
```

Prevents the addition of new properties to an object.

<!--Device-ObjectConstructor-preventExtensions<T>(o: T): T--><!--Device-ObjectConstructor-preventExtensions<T>(o: T): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |

## seal

```TypeScript
seal<T>(o: T): T
```

Prevents the modification of attributes of existing properties, and prevents the addition of new properties.

<!--Device-ObjectConstructor-seal<T>(o: T): T--><!--Device-ObjectConstructor-seal<T>(o: T): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |

## prototype

```TypeScript
readonly prototype: Object
```

A reference to the prototype for a class of objects.

**Type:** Object

<!--Device-ObjectConstructor-readonly prototype: Object--><!--Device-ObjectConstructor-readonly prototype: Object-End-->
