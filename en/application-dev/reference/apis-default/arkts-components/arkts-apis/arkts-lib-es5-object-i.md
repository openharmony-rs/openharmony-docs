# Object

```TypeScript
interface Object
```

## Modules to Import

```TypeScript
```

## hasOwnProperty

```TypeScript
hasOwnProperty(v: PropertyKey): boolean
```

Determines whether an object has a property with the specified name.

<!--Device-Object-hasOwnProperty(v: PropertyKey): boolean--><!--Device-Object-hasOwnProperty(v: PropertyKey): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | [PropertyKey](arkts-propertykey-t.md) | Yes |  |

## isPrototypeOf

```TypeScript
isPrototypeOf(v: Object): boolean
```

Determines whether an object exists in another object's prototype chain.

<!--Device-Object-isPrototypeOf(v: Object): boolean--><!--Device-Object-isPrototypeOf(v: Object): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | Object | Yes |  |

## propertyIsEnumerable

```TypeScript
propertyIsEnumerable(v: PropertyKey): boolean
```

Determines whether a specified property is enumerable.

<!--Device-Object-propertyIsEnumerable(v: PropertyKey): boolean--><!--Device-Object-propertyIsEnumerable(v: PropertyKey): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | [PropertyKey](arkts-propertykey-t.md) | Yes |  |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Returns a date converted to a string using the current locale.

<!--Device-Object-toLocaleString(): string--><!--Device-Object-toLocaleString(): string-End-->

## toString

```TypeScript
toString(): string
```

Returns a string representation of an object.

<!--Device-Object-toString(): string--><!--Device-Object-toString(): string-End-->

## valueOf

```TypeScript
valueOf(): Object
```

Returns the primitive value of the specified object.

<!--Device-Object-valueOf(): Object--><!--Device-Object-valueOf(): Object-End-->

## constructor

```TypeScript
constructor: Function
```

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

**Type:** Function

<!--Device-Object-constructor: Function--><!--Device-Object-constructor: Function-End-->
