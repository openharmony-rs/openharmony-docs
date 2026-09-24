# SharedArrayBuffer

```TypeScript
interface SharedArrayBuffer
```

## Modules to Import

```TypeScript
```

## slice

```TypeScript
slice(begin: number, end?: number): SharedArrayBuffer
```

Returns a section of an SharedArrayBuffer.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | Yes |  |
| end | number | No |  |

## [Symbol.species]

```TypeScript
readonly [Symbol.species]: SharedArrayBuffer
```

**Type:** SharedArrayBuffer

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "SharedArrayBuffer"
```

**Type:** "SharedArrayBuffer"

## byteLength

```TypeScript
readonly byteLength: number
```

Read-only. The length of the ArrayBuffer (in bytes).

**Type:** number
