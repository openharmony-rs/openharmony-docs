# InflateBackOutputCallback

```TypeScript
type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number
```

The output data provided by the user is written into the callback function. Whenever decompressed data is ready for output, zlib calls this function to write the data from the buffer to the target location.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outDesc | object | Yes | Object passed to output function. Object dependency requirement implementation. |
| buf | ArrayBuffer | Yes | Used to store data to be written. |
| length | number | Yes | Write the length of the output buffer. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return the number of bytes output. |
