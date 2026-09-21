# ObjectConstructor

```TypeScript
interface ObjectConstructor
```

## Modules to Import

```TypeScript
```

## entries

```TypeScript
entries<T>(o: { [s: string]: T } | ArrayLike<T>): [string, T][]
```

Returns an array of key/values of the enumerable properties of an object

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | { [s: string]: T } &#124; ArrayLike&lt;T&gt; | Yes |  |

<a id="entries-1"></a>

## entries

```TypeScript
entries(o: {}): [string, any][]
```

Returns an array of key/values of the enumerable properties of an object

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | {} | Yes |  |

## getOwnPropertyDescriptors

```TypeScript
getOwnPropertyDescriptors<T>(o: T): {[P in keyof T]: TypedPropertyDescriptor<T[P]>} & { [x: string]: PropertyDescriptor }
```

Returns an object containing all own property descriptors of an object

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | T | Yes |  |

## values

```TypeScript
values<T>(o: { [s: string]: T } | ArrayLike<T>): T[]
```

Returns an array of values of the enumerable properties of an object

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | { [s: string]: T } &#124; ArrayLike&lt;T&gt; | Yes |  |

<a id="values-1"></a>

## values

```TypeScript
values(o: {}): any[]
```

Returns an array of values of the enumerable properties of an object

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| o | {} | Yes |  |
