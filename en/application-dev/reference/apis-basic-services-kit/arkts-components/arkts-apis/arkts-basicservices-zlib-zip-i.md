# Zip

```TypeScript
interface Zip
```

Defines the **Zip** instance. It provides APIs to zip or unzip data in Zlib, Deflate, or Gzip format.

**Since:** 12

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## compress

```TypeScript
compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise<ZipOutputInfo>
```

Compresses the source buffer into the destination buffer. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dest | ArrayBuffer | Yes | Destination buffer. |
| source | ArrayBuffer | Yes | Source buffer. |
| sourceLen | number | No | Length of the source data. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ZipOutputInfo](arkts-basicservices-zlib-zipoutputinfo-i.md)&gt; | Promise used to return the result status and the total size of the destination buffer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world! Hello, world!';
const enc = util.TextEncoder.create('utf-8');
const u8 = enc.encodeInto(str);
const arrayBufferIn = u8.buffer.slice(u8.byteOffset, u8.byteOffset + u8.byteLength);

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress(arrayBufferOut, arrayBufferIn, 20).then((data) => {
  console.info('compress success:');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## compress2

```TypeScript
compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: number,): Promise<ZipOutputInfo>
```

Compresses the source buffer into the destination buffer. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dest | ArrayBuffer | Yes | Destination buffer. |
| source | ArrayBuffer | Yes | Source buffer. |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | Yes | For details, see [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md). |
| sourceLen | number | No | Length of the source data. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ZipOutputInfo](arkts-basicservices-zlib-zipoutputinfo-i.md)&gt; | Promise used to return the result status and the total size of the destination buffer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world! Hello, world!';
const enc = util.TextEncoder.create('utf-8');
const u8 = enc.encodeInto(str);
const arrayBufferIn = u8.buffer.slice(u8.byteOffset, u8.byteOffset + u8.byteLength);

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
  console.info('compress2 success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## compressBound

```TypeScript
compressBound(sourceLen: number): Promise<number>
```

Calculates the maximum size of the compressed data to be returned. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceLen | number | Yes | Length of the source data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the maximum size of the compressed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let zip = zlib.createZipSync();

zip.compressBound(str.length).then((data) => {
  console.info('compressBound success')
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## deflate

```TypeScript
deflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>
```

Deflates data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| flush | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | Yes | For details, see [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

## deflateBound

```TypeScript
deflateBound(strm: ZStream, sourceLength: number): Promise<number>
```

Calculates the maximum size of the compressed data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| sourceLength | number | Yes | Length of the source data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the maximum size of the compressed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateBound({ nextOut: arrayBufferOut }, 12).then((data) => {
    console.info('deflateBound success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateCopy

```TypeScript
deflateCopy(source: Zip): Promise<ReturnStatus>
```

Copies a compression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [Zip](arkts-basicservices-zlib-zip-i.md) | Yes | For details, see [Zip&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zip-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateCopy(zip).then((data) => {
    console.info('deflateCopy success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateEnd

```TypeScript
deflateEnd(strm: ZStream): Promise<ReturnStatus>
```

Releases all dynamically allocated data structs of a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateGetDictionary

```TypeScript
deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>
```

Obtains the content and length of the decompression dictionary used in a compression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| dictionary | ArrayBuffer | Yes | Buffer that receives the actual contents of the decompression dictionary. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DictionaryOutputInfo](arkts-basicservices-zlib-dictionaryoutputinfo-i.md)&gt; | Promise used to return the result status and length of the dictionary. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateGetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateInit

```TypeScript
deflateInit(strm: ZStream, level: CompressLevel): Promise<ReturnStatus>
```

Initializes a compression stream with a specified compression level. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | Yes | For details, see [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

## deflateInit2

```TypeScript
deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: number,
        memLevel: MemLevel, strategy: CompressStrategy): Promise<ReturnStatus>
```

Initializes a compression stream with the specified compression level, compression method, window size, memory level, and compression strategy. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | Yes | For details, see [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md). |
| method | [CompressMethod](arkts-basicservices-zlib-compressmethod-e.md) | Yes | For details, see [CompressMethod](arkts-basicservices-zlib-compressmethod-e.md). |
| windowBits | number | Yes | Memory window size. The value is restricted in certain range based on the data formats. The options are as follows:<br>Zlib: [1, 15]<br>Gzip: (15, +∞)<br>Raw Deflate: [-15, -1] |
| memLevel | [MemLevel](arkts-basicservices-zlib-memlevel-e.md) | Yes | For details, see [MemLevel](arkts-basicservices-zlib-memlevel-e.md). |
| strategy | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | Yes | For details, see [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit2(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED, zlib.CompressMethod.DEFLATED, 28,
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
      console.info('deflateInit2 success');
    }).catch((errData: BusinessError) => {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
    })
}
```

## deflateParams

```TypeScript
deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>
```

Dynamically updates the compression level and compression strategy. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | Yes | For details, see [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md). |
| strategy | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | Yes | For details, see [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateParams(zStream, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
    console.info('deflateParams success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflatePending

```TypeScript
deflatePending(strm: ZStream): Promise<DeflatePendingOutputInfo>
```

Returns the number of bytes and bits of output that has been generated but not yet provided in the available output. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeflatePendingOutputInfo](arkts-basicservices-zlib-deflatependingoutputinfo-i.md)&gt; | Promise used to return the result status, and number of bits and bytes for output. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflatePending({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflatePending success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflatePrime

```TypeScript
deflatePrime(strm: ZStream, bits: number, value: number): Promise<ReturnStatus>
```

Inserts bits and values into the compression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| bits | number | Yes | Number of bits to be inserted. The value ranges from 0 to 16. |
| value | number | Yes | Bit value corresponding to the number of bits. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflatePrime({ nextOut: arrayBufferOut }, 5, 2).then((data) => {
    console.info('deflatePrime success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateReset

```TypeScript
deflateReset(strm: ZStream): Promise<ReturnStatus>
```

Equivalent to call the **deflateEnd** API and then the **deflateInit** API. However, this API does not release or reallocate the internal decompression state. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateReset({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflateReset success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateResetKeep

```TypeScript
deflateResetKeep(strm: ZStream): Promise<ReturnStatus>
```

Resets the initialized compression stream, but retains the compression parameters and dictionaries set by it. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateResetKeep({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflateResetKeep success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateSetDictionary

```TypeScript
deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>
```

Initializes the compression dictionary from a given sequence of bytes. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| dictionary | ArrayBuffer | Yes | Dictionary data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## deflateSetHeader

```TypeScript
deflateSetHeader(strm: ZStream, head: GzHeader): Promise<ReturnStatus>
```

Provides the header information of a gzip file when **deflateInit2()** requests a gzip stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| head | [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | Yes | Header information of a gzip file extracted from the compressed data stream. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit2(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED, zlib.CompressMethod.DEFLATED, 28,
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
      console.info('deflateInit2 success');
    }).catch((errData: BusinessError) => {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
    })
  await zip.deflateSetHeader({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then((data) => {
    console.info('deflateSetHeader success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

## deflateTune

```TypeScript
deflateTune(strm: ZStream, goodLength: number, maxLazy: number, niceLength: number, maxChain: number): Promise<ReturnStatus>
```

Fine-tunes the internal compression parameters of **deflate**. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| goodLength | number | Yes | Matched length threshold. |
| maxLazy | number | Yes | Delay matching strategy used when the compression algorithm builds a Huffman tree. The value is an integer ranging from 0 to 4. **1**–**4**: A larger value indicates a lazier algorithm, which performs a slower matching process but generates a better compression result. **0**: Lazy matching is disabled. The algorithm builds a Huffman tree as soon as possible. The compression speed is fast, but the compression ratio is low. |
| niceLength | number | Yes | Appropriate delay length threshold. |
| maxChain | number | Yes | Maximum chain length. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateTune({ nextOut: arrayBufferOut }, 2, 2, 2, 2).then((data) => {
    console.info('deflateTune success:')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## getZStream

```TypeScript
getZStream(): Promise<ZStream>
```

Obtains this stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ZStream](arkts-basicservices-zlib-zstream-i.md)&gt; | Promise used to return the **ZStream** object. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.getZStream().then(data => {
  console.info('getZStream success');
})
```

## inflate

```TypeScript
inflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>
```

Inflates data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| flush | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | Yes | For details, see [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../errorcode-zlib.md#17800005-incorrect-input-data) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflate({ availableIn: 8, availableOut: 8 }, 0).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateBack

```TypeScript
inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise<ReturnStatus>
```

Implements decompression and uses callbacks to process input and output data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| backIn | [InflateBackInputCallback](arkts-basicservices-zlib-inflatebackinputcallback-t.md) | Yes | A function used to decompress data from the end of the array to read the original compressed data from the input source. |
| inDesc | object | Yes | Common object. |
| backOut | [InflateBackOutputCallback](arkts-basicservices-zlib-inflatebackoutputcallback-t.md) | Yes | Writes the decompressed data to the destination buffer. |
| outDesc | object | Yes | Common object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let readIn: (inDesc: object) => ArrayBuffer = (inDesc: object): ArrayBuffer => {
    console.info("inDesc = ", JSON.stringify(inDesc));
    let buffer = new ArrayBuffer(26)
    let array = new Uint8Array(buffer);
    array.set([31, 139, 8, 0, 0, 0, 0, 0, 0, 10, 243, 72, 205, 201, 201, 231, 2, 0, 22, 53, 150, 49, 6, 0, 0, 0]);
    return buffer;
  }

  let writeOut: (outDesc: object, buffer: ArrayBuffer, length: number) => number = (outDesc: object, buffer: ArrayBuffer, length: number): number => {
    console.info("outDesc = ", outDesc);
    console.info("buffer = ", buffer);
    console.info("length = ", length);
    let array = new Uint8Array(buffer);
    let dataString = "";
    for (let i = 0; i < length; i++) {
      dataString += String.fromCharCode(array[i]);
    }
    console.info('writeOut ', dataString);
    return 0;
  }

  let have = 0;
  let first = 1;
  let arrayBuffer = new ArrayBuffer(26);
  let next = new Uint8Array(arrayBuffer);
  let last = 0;
  let index = 0;
  let flags = 0;
  let NEXT2: () => number = (): number => {
    let o6: object = new Object()
    if (!have) {
      arrayBuffer = readIn(o6)
      next = new Uint8Array(arrayBuffer);
      console.info('readIn next = ', next.length)
      have = next.length;
    }
    if (have) {
      have--;
      last = next[index];
      index++;
    }
    else {
      last = -1;
    }
    return last;
  }

  let inflateBackTest: () => void = (async () => {
    try {
      have = 0;
      first = 1;
      arrayBuffer = new ArrayBuffer(26);
      next = new Uint8Array(arrayBuffer);
      last = 0;
      index = 0;
      flags = 0;
      let sr = zlib.createZipSync();
      let buffer = new ArrayBuffer(1024)
      await sr.inflateBackInit({}, 15, buffer).then((result) => {
        console.info('inflateBackInit Call result res', result)
      })
      let ret = 0;
      for (; ;) {
        if (NEXT2() == -1) {
          ret = 0;
          console.info('inflateBackTest Call result NEXT2() == -1')
          break;
        }
        console.info('have =  last = ', have, last)
        if (last != 31 || NEXT2() != 139 ) {
          ret = first ? -3 : -1;
          console.info('inflateBackTest Call result last != 31 || (NEXT2() != 139 && last != 157)')
          break;
        }
        first = 0;
        ret = -5;
        if (NEXT2() != 8) {
          if (last < 0) {
            console.info('inflateBackTest Call result 1 last == -1')
            break;
          }
        }
        flags = NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        if (last < 0) {
          console.info('inflateBackTest Call result 2 last == -1')
          break;
        }
        console.info('index =  have = ', next[index], have)
        let newArrayBuffer = new ArrayBuffer(have);
        let newNext = new Uint8Array(newArrayBuffer);
        for (let i = 0; i < have; i++) {
          newNext[i] = next[26 - have + i];
        }
        console.info('newArrayBuffer.length = ', newArrayBuffer.byteLength)
        console.info('newNext.length = ', newNext.length)
        let zStream: zlib.ZStream = {
          nextIn: newArrayBuffer,
          availableIn: have,
        };
        await sr.inflateBack(
          zStream,
          readIn,
          { fileName: 'test.gz' },
          writeOut,
          { fileName: 'test.gz' }).then((result) => {
            ret = result;
            console.info('inflateBack Call result res', result)
          })
        if (ret == 1) {
          console.info('inflateBackTest Call result success')
          break;
        }
      }
      await sr.inflateBackEnd({}).then((result) => {
        console.info('inflateBackEnd Call result res', result)
      })
    }
    catch (errData) {
      console.error(`errData is message:${errData}`);
    }
  })
  inflateBackTest();
}
```

## inflateBackEnd

```TypeScript
inflateBackEnd(strm: ZStream): Promise<ReturnStatus>
```

Releases all memory allocated by the **inflateBackInit()** function. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

For details about the sample code, see [inflateBack](#inflateback).

## inflateBackInit

```TypeScript
inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise<ReturnStatus>
```

Initializes the internal stream state for decompression before using the **inflateBack()** function. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| windowBits | number | Yes | Memory window size. The value is restricted in certain range based on the data formats. The options are as follows:<br>Zlib: [1, 15]<br>Gzip: (15, +∞)<br>Raw Deflate: [-15, -1] |
| window | ArrayBuffer | Yes | Preset window buffer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

For details about the sample code, see [inflateBack](#inflateback).

## inflateCodesUsed

```TypeScript
inflateCodesUsed(strm: ZStream): Promise<number>
```

Describes the number of Huffman trees used in a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of Huffman trees that have been used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateCodesUsed({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 8 }).then(data => {
    console.info('inflateCodesUsed success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateCopy

```TypeScript
inflateCopy(source: Zip): Promise<ReturnStatus>
```

Copies a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [Zip](arkts-basicservices-zlib-zip-i.md) | Yes | For details, see [Zip&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zip-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  let destZip = zlib.createZipSync();
  await destZip.inflateCopy(zip).then((data) => {
    console.info('inflateCopy success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateEnd

```TypeScript
inflateEnd(strm: ZStream): Promise<ReturnStatus>
```

Releases all dynamically allocated data structs of a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflate({ availableIn: 8, availableOut: 8 }, 0).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateGetDictionary

```TypeScript
inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>
```

Obtains the content and length of the decompression dictionary used in a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| dictionary | ArrayBuffer | Yes | Receives the actual contents of the decompression dictionary. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DictionaryOutputInfo](arkts-basicservices-zlib-dictionaryoutputinfo-i.md)&gt; | Promise used to return the result status and length of the dictionary. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
  ).then(data => {
    console.info('inflateInit2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('inflateGetDictionary success:')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateGetHeader

```TypeScript
inflateGetHeader(strm: ZStream, header: GzHeader): Promise<ReturnStatus>
```

Obtains the header information of a gzip file before decompressing data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| header | [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | Yes | Header information of a gzip file extracted from the compressed data stream. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
  ).then(data => {
    console.info('inflateInit2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateGetHeader({ availableIn: 1, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then(data => {
    console.info('inflateGetHeader success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateInit

```TypeScript
inflateInit(strm: ZStream): Promise<ReturnStatus>
```

Initializes a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
).then(data => {
  console.info('inflateInit success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## inflateInit2

```TypeScript
inflateInit2(strm: ZStream, windowBits: number): Promise<ReturnStatus>
```

Initializes a decompression stream with the specified **windowBits**. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| windowBits | number | Yes | Memory window size. The value is restricted in certain range based on the data formats. The options are as follows:<br>Zlib: [1, 15]<br>Gzip: (15, +∞)<br>Raw Deflate: [-15, -1] |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
).then(data => {
  console.info('inflateInit2 success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## inflateMark

```TypeScript
inflateMark(strm: ZStream): Promise<number>
```

Marks the location of the input data for random access. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the current location. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateMark({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }).then(data => {
    console.info('inflateMark success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflatePrime

```TypeScript
inflatePrime(strm: ZStream, bits: number, value: number): Promise<ReturnStatus>
```

Sets the initial number of bits and bit value in the specified decompression stream to pre-fill the bit buffer at the beginning of the decompression stream to correctly process the data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| bits | number | Yes | Number of bits to be written to the bit buffer. |
| value | number | Yes | Bit value used to fill the bit buffer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflatePrime({ nextOut: arrayBufferOut }, 5, 2).then(data => {
    console.info('inflatePrime success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateReset

```TypeScript
inflateReset(strm: ZStream): Promise<ReturnStatus>
```

Resets the status of the specified decompression stream to the initial state to start a new decompression operation. The internal buffer is not released or reallocated. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateReset({ availableIn: 1, availableOut: 8 }).then(data => {
    console.info('inflateReset success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateReset2

```TypeScript
inflateReset2(strm: ZStream, windowBits: number): Promise<ReturnStatus>
```

Resets the status of the specified decompression stream and updates the window size to start a new decompression operation. The internal buffer is not released or reallocated. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| windowBits | number | Yes | Memory window size. The value is restricted in certain range based on the data formats. The options are as follows:<br>Zlib: [1, 15]<br>Gzip: (15, +∞)<br>Raw Deflate: [-15, -1] |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateReset2({ availableOut: 8 }, 15).then(data => {
    console.info('inflateReset2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateResetKeep

```TypeScript
inflateResetKeep(strm: ZStream): Promise<ReturnStatus>
```

Resets the state of the decompression stream to retain the allocated Huffman tree and preset dictionary. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateResetKeep({ availableIn: 1 }).then(data => {
    console.info('inflateResetKeep success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateSetDictionary

```TypeScript
inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>
```

Initializes the dictionary content of a decompression stream based on the given dictionary data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| dictionary | ArrayBuffer | Yes | Dictionary data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../errorcode-zlib.md#17800005-incorrect-input-data) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello, hello!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  let dictionary = 'hello'
  let dictionarybuf = new ArrayBuffer(dictionary.length);
  let dictionarybufdata = new Uint8Array(dictionarybuf);
  for (let i = 0, j = dictionary.length; i < j; i++) {
    dictionarybufdata[i] = str.charCodeAt(i);
  }
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_BEST_COMPRESSION).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateSetDictionary({}, dictionarybuf).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 14, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({}).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  try {
    await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 100 }).then(data => {
      console.info('inflateInit success')
    })
  } catch (errData) {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  }
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.inflateSetDictionary({}, dictionarybuf).then((data) => {
    console.info('inflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

## inflateSync

```TypeScript
inflateSync(strm: ZStream): Promise<ReturnStatus>
```

Skips invalid compressed data until a possible complete refresh point is found. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../errorcode-zlib.md#17800005-incorrect-input-data) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello, hello!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 3, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FULL_FLUSH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflate({ availableIn: 11 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateEnd({}).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  try {
    await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 2 }).then(data => {
      console.info('inflateInit2 success')
    })
  } catch (errData) {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  }
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateSync({ availableIn: 26 }).then(data => {
    console.info('inflateSync success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateSyncPoint

```TypeScript
inflateSyncPoint(strm: ZStream): Promise<ReturnStatus>
```

Finds the synchronization point of a decompression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateSyncPoint({ availableIn: 1 }).then(data => {
    console.info('inflateSyncPoint success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## inflateValidate

```TypeScript
inflateValidate(strm: ZStream, check: number): Promise<ReturnStatus>
```

Validates the checksum inside the compression stream. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | Yes | For details, see [ZStream&lt;sup&gt;12+&lt;/sup&gt;](arkts-basicservices-zlib-zstream-i.md). |
| check | number | Yes | Expected checksum. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)&gt; | Promise used to return the result status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../errorcode-zlib.md#17800004-compressed-or-decompressed-flow-error) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateValidate({ availableIn: 1 }, 1).then(data => {
    console.info('inflateValidate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## uncompress

```TypeScript
uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise<ZipOutputInfo>
```

Decompresses the compressed data into the raw data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dest | ArrayBuffer | Yes | Destination buffer. |
| source | ArrayBuffer | Yes | Source buffer. |
| sourceLen | number | No | Length of the source data. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ZipOutputInfo](arkts-basicservices-zlib-zipoutputinfo-i.md)&gt; | Promise used to return the result status and the total size of the destination buffer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800005](../errorcode-zlib.md#17800005-incorrect-input-data) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.compress(arrayBufferOut, arrayBufferIn, 12).then((data) => {
    console.info('compress success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.uncompress(arrayBufferIn, arrayBufferOut, 20).then((data) => {
    console.info('uncompress success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## uncompress2

```TypeScript
uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise<DecompressionOutputInfo>
```

Decompresses the compressed data into the raw data. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dest | ArrayBuffer | Yes | Destination buffer. |
| source | ArrayBuffer | Yes | Source buffer. |
| sourceLen | number | No | Length of the source data. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DecompressionOutputInfo](arkts-basicservices-zlib-decompressionoutputinfo-i.md)&gt; | Promise used to return the result status, total size of the destination buffer, and the length of the source data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800005](../errorcode-zlib.md#17800005-incorrect-input-data) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../errorcode-zlib.md#17800007-incorrect-input-buffer) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Examples**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('compress2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.uncompress2(arrayBufferIn, arrayBufferOut, 20).then((data) => {
    console.info('uncompress2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## zlibCompileFlags

```TypeScript
zlibCompileFlags(): Promise<number>
```

Returns the flags indicating compile-time options. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the flags indicating compile-time options. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibCompileFlags().then((data) => {
  console.info('zlibCompileFlags success')
})
```

## zlibVersion

```TypeScript
zlibVersion(): Promise<string>
```

Obtains the version information of this zlib library connected. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the version of the current zlib library. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibVersion().then((data) => {
  console.info('zlibVersion success')
})
```
