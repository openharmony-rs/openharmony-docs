# ArrayBuffer

Represents a raw buffer of binary data, which is used to store data for the different typed arrays. ArrayBuffers cannot be read from or written to directly, but can be passed to a typed array or DataView Object to interpret the raw buffer as needed.

## Modules to Import

```TypeScript
```

## slice

```TypeScript
slice(begin: number, end?: number): ArrayBuffer
```

Returns a section of an ArrayBuffer.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | Yes |  |
| end | number | No |  |

## byteLength

```TypeScript
readonly byteLength: number
```

Read-only. The length of the ArrayBuffer (in bytes).

**Type:** number
