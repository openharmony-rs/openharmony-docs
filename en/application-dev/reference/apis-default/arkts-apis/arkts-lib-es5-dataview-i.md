# DataView

## Modules to Import

```TypeScript
```

## getFloat32

```TypeScript
getFloat32(byteOffset: number, littleEndian?: boolean): number
```

Gets the Float32 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getFloat64

```TypeScript
getFloat64(byteOffset: number, littleEndian?: boolean): number
```

Gets the Float64 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getInt16

```TypeScript
getInt16(byteOffset: number, littleEndian?: boolean): number
```

Gets the Int16 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getInt32

```TypeScript
getInt32(byteOffset: number, littleEndian?: boolean): number
```

Gets the Int32 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getInt8

```TypeScript
getInt8(byteOffset: number): number
```

Gets the Int8 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |

## getUint16

```TypeScript
getUint16(byteOffset: number, littleEndian?: boolean): number
```

Gets the Uint16 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getUint32

```TypeScript
getUint32(byteOffset: number, littleEndian?: boolean): number
```

Gets the Uint32 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getUint8

```TypeScript
getUint8(byteOffset: number): number
```

Gets the Uint8 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |

## setFloat32

```TypeScript
setFloat32(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Float32 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setFloat64

```TypeScript
setFloat64(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Float64 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setInt16

```TypeScript
setInt16(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Int16 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setInt32

```TypeScript
setInt32(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Int32 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setInt8

```TypeScript
setInt8(byteOffset: number, value: number): void
```

Stores an Int8 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |

## setUint16

```TypeScript
setUint16(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Uint16 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setUint32

```TypeScript
setUint32(byteOffset: number, value: number, littleEndian?: boolean): void
```

Stores an Uint32 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |
| littleEndian | boolean | No |  |

## setUint8

```TypeScript
setUint8(byteOffset: number, value: number): void
```

Stores an Uint8 value at the specified byte offset from the start of the view.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | number | Yes |  |

## buffer

```TypeScript
readonly buffer: ArrayBuffer
```

**Type:** ArrayBuffer

## byteLength

```TypeScript
readonly byteLength: number
```

**Type:** number

## byteOffset

```TypeScript
readonly byteOffset: number
```

**Type:** number
