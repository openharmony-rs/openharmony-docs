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

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | [PropertyKey](arkts-propertykey-t.md) | Yes |  |

## isPrototypeOf

```TypeScript
isPrototypeOf(v: Object): boolean
```

Determines whether an object exists in another object's prototype chain.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | Object | Yes |  |

## propertyIsEnumerable

```TypeScript
propertyIsEnumerable(v: PropertyKey): boolean
```

Determines whether a specified property is enumerable.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | [PropertyKey](arkts-propertykey-t.md) | Yes |  |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Returns a date converted to a string using the current locale.

## toString

```TypeScript
toString(): string
```

Returns a string representation of an object.

## valueOf

```TypeScript
valueOf(): Object
```

Returns the primitive value of the specified object.

## constructor

```TypeScript
constructor: Function
```

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

**Type:** Function
