# Blob

```TypeScript
class Blob
```

Process data as blob type

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## arrayBuffer

```TypeScript
arrayBuffer(): Promise<ArrayBuffer>
```

Puts the **Blob** data into an **ArrayBuffer** object. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; |  |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.arrayBuffer();
pro.then((val: ArrayBuffer) => {
  let uint8Array: Uint8Array = new Uint8Array(val);
  console.info(uint8Array.toString());
  // Output: 97,98,99
});
```

## constructor

```TypeScript
constructor(sources: string[] | ArrayBuffer[] | TypedArray[] | DataView[] | Blob[], options?: Object)
```

A constructor used to create a **Blob** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sources | string[] &#124; ArrayBuffer[] &#124; TypedArray[] &#124; DataView[] &#124; [Blob](arkts-arkts-buffer-blob-c.md)[] | Yes | Data sources of the **Blob** object. |
| options | Object | No | options:<br>- **endings**: specifies how the terminator **'\n'** is output. The value can be **'native'** or **'transparent'**. **'native'** means that the terminator follows the system. **'transparent'** means that the terminator stored in the **Blob** object remains unchanged. The default value is **'transparent'**.<br>- **type**: type of the data in the **Blob** object. This type represents the MIME type of the data. However, it is not used for type format validation. The default value is **''**. |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob  = new buffer.Blob(['a', 'b', 'c']);

class option {
  endings: string = "";
  type: string = "";
}
let o1: option = {endings:'native', type: 'MIME'}
let blob1: buffer.Blob = new buffer.Blob(['a', 'b', 'c'], o1);
```

## slice

```TypeScript
slice(start?: number, end?: number, type?: string): Blob
```

Creates and returns a **Blob** object that contains specified data from this **Blob** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | Offset to the start position of data. The default value is **0**. |
| end | number | No | Offset to the end position of data. The default value is the data length in the original **Blob** object. |
| type | string | No | Type of the data in the new **Blob** object. The default value is **''**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Blob](arkts-arkts-buffer-blob-c.md) |  |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let blob2 = blob.slice(0, 2);
let blob3 = blob.slice(0, 2, "MIME");
console.info("type:", blob3.type); // type: MIME
```

## text

```TypeScript
text(): Promise<string>
```

Decodes data using UTF-8 and returns a string. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; |  |

**Examples**

```TypeScript
import { buffer } from '@kit.ArkTS';

let blob: buffer.Blob = new buffer.Blob(['a', 'b', 'c']);
let pro = blob.text();
pro.then((val: string) => {
  console.info(val);
  // Output: abc
});
```

## size

```TypeScript
get size(): number
```

Total size of the Blob instance, in bytes.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## type

```TypeScript
get type(): string
```

Type of the data in the Blob instance.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
