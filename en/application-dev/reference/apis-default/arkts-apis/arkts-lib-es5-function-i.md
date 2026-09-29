# Function

```TypeScript
interface Function
```

Creates a new function.

<!--Device-unnamed-interface Function--><!--Device-unnamed-interface Function-End-->

## Modules to Import

```TypeScript
```

## apply

```TypeScript
apply(this: Function, thisArg: any, argArray?: any): any
```

Calls the function, substituting the specified object for the this value of the function, and the specified array for the arguments of the function.

<!--Device-Function-apply(this: Function, thisArg: any, argArray?: any): any--><!--Device-Function-apply(this: Function, thisArg: any, argArray?: any): any-End-->

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

<!--Device-Function-bind(this: Function, thisArg: any, ...argArray: any[]): any--><!--Device-Function-bind(this: Function, thisArg: any, ...argArray: any[]): any-End-->

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

<!--Device-Function-call(this: Function, thisArg: any, ...argArray: any[]): any--><!--Device-Function-call(this: Function, thisArg: any, ...argArray: any[]): any-End-->

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

<!--Device-Function-toString(): string--><!--Device-Function-toString(): string-End-->

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
