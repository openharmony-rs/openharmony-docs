# Function

```TypeScript
interface Function
```

Creates a new function.

## Modules to Import

```TypeScript
```

## apply

```TypeScript
apply(this: Function, thisArg: any, argArray?: any): any
```

Calls the function, substituting the specified object for the this value of the function, and the specified array for the arguments of the function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | Function | Yes |  |
| thisArg | any | Yes |  |
| argArray | any | No |  |

## bind

```TypeScript
bind(this: Function, thisArg: any, ...argArray: any[]): any
```

For a given function, creates a bound function that has the same body as the original function. The this object of the bound function is associated with the specified object, and has the specified initial parameters.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | Function | Yes |  |
| thisArg | any | Yes |  |
| argArray | any[] | Yes |  |

## call

```TypeScript
call(this: Function, thisArg: any, ...argArray: any[]): any
```

Calls a method of an object, substituting another object for the current object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | Function | Yes |  |
| thisArg | any | Yes |  |
| argArray | any[] | Yes |  |

## toString

```TypeScript
toString(): string
```

Returns a string representation of a function.

## arguments

```TypeScript
arguments: any
```

**Type:** any

## caller

```TypeScript
caller: Function
```

**Type:** Function

## length

```TypeScript
readonly length: number
```

**Type:** number

## prototype

```TypeScript
prototype: any
```

**Type:** any
