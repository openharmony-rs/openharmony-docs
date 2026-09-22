# ArrayConstructor

```TypeScript
interface ArrayConstructor
```

## Modules to Import

```TypeScript
```

## [[Call]]

```TypeScript
(arrayLength?: number): any[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | No |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
<T>(arrayLength: number): T[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | Yes |  |

<a id="call-2"></a>

## [[Call]]

```TypeScript
<T>(...items: T[]): T[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes |  |

## [[Construct]]

```TypeScript
new(arrayLength?: number): any[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | No |  |

<a id="construct-1"></a>

## [[Construct]]

```TypeScript
new <T>(arrayLength: number): T[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | Yes |  |

<a id="construct-2"></a>

## [[Construct]]

```TypeScript
new <T>(...items: T[]): T[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes |  |

## isArray

```TypeScript
isArray(arg: any): arg is any[]
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arg | any | Yes |  |

## prototype

```TypeScript
readonly prototype: any[]
```

**Type:** any[]
