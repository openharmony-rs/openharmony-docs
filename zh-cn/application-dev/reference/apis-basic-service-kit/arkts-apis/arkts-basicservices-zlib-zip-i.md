# Zip

压缩解压缩对象实例，支持以zlib、deflate、gzip格式对数据进行压缩与解压。

**起始版本：** 12

<!--Device-zlib-interface Zip--><!--Device-zlib-interface Zip-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## compress

```TypeScript
compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise<ZipOutputInfo>
```

将源缓冲区压缩到目标缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<ZipOutputInfo>--><!--Device-Zip-compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<ZipOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dest | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 目标缓冲区。 |
| source | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 源数据缓冲区。 |
| sourceLen | number | 否 | 源数据长度。默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ZipOutputInfo> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

```TypeScript
import { util } from '@kit.ArkTS';
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world! 你好，世界！';
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

将源缓冲区压缩到目标缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: long,): Promise<ZipOutputInfo>--><!--Device-Zip-compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: long,): Promise<ZipOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dest | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 目标缓冲区。 |
| source | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 源数据缓冲区。 |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 是 | 参考[CompressLevel枚举定义](arkts-basicservices-zlib-compresslevel-e.md)。 |
| sourceLen | number | 否 | 源数据长度。默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ZipOutputInfo> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

## compressBound

```TypeScript
compressBound(sourceLen: number): Promise<number>
```

计算返回压缩大小的上限。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-compressBound(sourceLen: int): Promise<int>--><!--Device-Zip-compressBound(sourceLen: int): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceLen | number | 是 | 源数据长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回压缩大小的上限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

压缩数据。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>--><!--Device-Zip-deflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| flush | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | 是 | 参考[CompressFlushMode定义](arkts-basicservices-zlib-compressflushmode-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

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

计算压缩大小的上限。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateBound(strm: ZStream, sourceLength: long): Promise<int>--><!--Device-Zip-deflateBound(strm: ZStream, sourceLength: long): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| sourceLength | number | 是 | 源数据长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回压缩大小的上限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

复制压缩流。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateCopy(source: Zip): Promise<ReturnStatus>--><!--Device-Zip-deflateCopy(source: Zip): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Zip](arkts-basicservices-zlib-zip-i.md) | 是 | 参考[Zip定义](arkts-basicservices-zlib-zip-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

解压流的所有动态分配的数据结构都被释放。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateEnd(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-deflateEnd(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

获取当前压缩流中使用的解压缩字典内容及其长度。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>--><!--Device-Zip-deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| dictionary | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 接收压缩字典的实际内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DictionaryOutputInfo> | Promise对象。返回结果状态和字典的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

初始化压缩流并设置指定压缩级别。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateInit(strm: ZStream, level: CompressLevel): Promise<ReturnStatus>--><!--Device-Zip-deflateInit(strm: ZStream, level: CompressLevel): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 是 | 参考[CompressLevel枚举定义](arkts-basicservices-zlib-compresslevel-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

初始化压缩流并设置压缩级别、压缩方法、窗口大小、内存级别和压缩策略。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: int,
        memLevel: MemLevel, strategy: CompressStrategy): Promise<ReturnStatus>--><!--Device-Zip-deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: int,
        memLevel: MemLevel, strategy: CompressStrategy): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 是 | 参考[CompressLevel枚举定义](arkts-basicservices-zlib-compresslevel-e.md)。 |
| method | [CompressMethod](arkts-basicservices-zlib-compressmethod-e.md) | 是 | 参考[CompressMethod枚举定义](arkts-basicservices-zlib-compressmethod-e.md)。 |
| windowBits | number | 是 | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。 |
| memLevel | [MemLevel](arkts-basicservices-zlib-memlevel-e.md) | 是 | 参考[MemLevel枚举定义](arkts-basicservices-zlib-memlevel-e.md)。 |
| strategy | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | 是 | 参考[CompressStrategy枚举定义](arkts-basicservices-zlib-compressstrategy-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

动态更新压缩级别和压缩策略。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>--><!--Device-Zip-deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 是 | 参考[CompressLevel枚举定义](arkts-basicservices-zlib-compresslevel-e.md)。 |
| strategy | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | 是 | 参考[CompressStrategy枚举定义](arkts-basicservices-zlib-compressstrategy-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

返回已生成但尚未在可用输出中提供的输出的字节数和位数。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflatePending(strm: ZStream): Promise<DeflatePendingOutputInfo>--><!--Device-Zip-deflatePending(strm: ZStream): Promise<DeflatePendingOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DeflatePendingOutputInfo> | Promise对象。返回结果状态、输出位数和输出字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

在压缩流中插入位和值。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflatePrime(strm: ZStream, bits: int, value: int): Promise<ReturnStatus>--><!--Device-Zip-deflatePrime(strm: ZStream, bits: int, value: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| bits | number | 是 | 要插入的位数，取值范围在0~16。 |
| value | number | 是 | 与位数相对应的位值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

这个函数相当于先调用deflateEnd再调用deflateInit，但是并不会释放和重新分配内部解压缩状态。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateReset(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-deflateReset(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

重置初始化的deflate压缩流，但保留其设置的压缩参数和字典。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateResetKeep(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-deflateResetKeep(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

从给定的字节序列初始化压缩字典。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>--><!--Device-Zip-deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| dictionary | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 字典数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

当deflateInit2()请求gzip流时，提供gzip标头信息。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateSetHeader(strm: ZStream, head: GzHeader): Promise<ReturnStatus>--><!--Device-Zip-deflateSetHeader(strm: ZStream, head: GzHeader): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| head | [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | 是 | 从压缩数据流中提取的gzip头信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

微调deflate的内部压缩参数。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-deflateTune(strm: ZStream, goodLength: int, maxLazy: int, niceLength: int, maxChain: int): Promise<ReturnStatus>--><!--Device-Zip-deflateTune(strm: ZStream, goodLength: int, maxLazy: int, niceLength: int, maxChain: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| goodLength | number | 是 | 匹配的长度阈值。 |
| maxLazy | number | 是 | 压缩算法在构建哈夫曼树时的延迟匹配策略，取值范围为0到4的整数。1到4，值越大，算法越‘懒’，匹配过程越慢，但可能生成更优的压缩结果。0：禁用懒惰匹配，算法会尽快构建哈夫曼树，压缩速度快，但压缩率低。 |
| niceLength | number | 是 | 适合的延迟长度阈值。 |
| maxChain | number | 是 | 最大链条长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

输出流。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-getZStream(): Promise<ZStream>--><!--Device-Zip-getZStream(): Promise<ZStream>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ZStream> | Promise对象。返回ZStream流。 |

**示例：**

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

解压数据。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>--><!--Device-Zip-inflate(strm: ZStream, flush: CompressFlushMode): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| flush | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | 是 | 参考[CompressFlushMode定义](arkts-basicservices-zlib-compressflushmode-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../../apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**示例：**

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

实现原始解压缩，采用回调接口来处理输入和输出。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise<ReturnStatus>--><!--Device-Zip-inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| backIn | [InflateBackInputCallback](arkts-basicservices-zlib-inflatebackinputcallback-t.md) | 是 | 一种函数，用于从末尾解压缩数据，以从输入源读取原始压缩数据。 |
| inDesc | object | 是 | 通用对象。 |
| backOut | [InflateBackOutputCallback](arkts-basicservices-zlib-inflatebackoutputcallback-t.md) | 是 | 将解压缩的数据写入目标输出。 |
| outDesc | object | 是 | 通用对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

inflateBackInit()函数分配的所有内存都被释放。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateBackEnd(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateBackEnd(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

参考[inflateBack](#inflateback12)中的示例代码。

## inflateBackInit

```TypeScript
inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise<ReturnStatus>
```

使用inflateBack()函数前初始化内部流状态以进行解压缩。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateBackInit(strm: ZStream, windowBits: long, window: ArrayBuffer): Promise<ReturnStatus>--><!--Device-Zip-inflateBackInit(strm: ZStream, windowBits: long, window: ArrayBuffer): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| windowBits | number | 是 | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。 |
| window | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 预设的窗口缓冲区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

参考[inflateBack](#inflateback12)中的示例代码。

## inflateCodesUsed

```TypeScript
inflateCodesUsed(strm: ZStream): Promise<number>
```

当前解压缩流中使用的霍夫曼编码树的数量。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateCodesUsed(strm: ZStream): Promise<long>--><!--Device-Zip-inflateCodesUsed(strm: ZStream): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回已使用的霍夫曼编码树的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

复制解压流。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateCopy(source: Zip): Promise<ReturnStatus>--><!--Device-Zip-inflateCopy(source: Zip): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Zip](arkts-basicservices-zlib-zip-i.md) | 是 | 参考[Zip定义](arkts-basicservices-zlib-zip-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

解压流的所有动态分配的数据结构都被释放。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateEnd(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateEnd(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

获取当前解压缩流中使用的解压缩字典内容及其长度。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>--><!--Device-Zip-inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<DictionaryOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| dictionary | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 接收解压缩字典的实际内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DictionaryOutputInfo> | Promise对象。返回结果状态和字典的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

用于在解压缩数据前设置gzip文件头部信息。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateGetHeader(strm: ZStream, header: GzHeader): Promise<ReturnStatus>--><!--Device-Zip-inflateGetHeader(strm: ZStream, header: GzHeader): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| header | [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | 是 | 从压缩数据流中提取的gzip头信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

初始化解压缩流。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateInit(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateInit(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

初始化解压缩流并设置指定的 windowBits 参数。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateInit2(strm: ZStream, windowBits: int): Promise<ReturnStatus>--><!--Device-Zip-inflateInit2(strm: ZStream, windowBits: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| windowBits | number | 是 | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

用于标记输入数据中的位置以供随机访问。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateMark(strm: ZStream): Promise<int>--><!--Device-Zip-inflateMark(strm: ZStream): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

在指定解压缩流中设置初始比特数和比特值，用于在解压流开始时预填充比特缓冲区，以正确处理流起始位置的数据。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflatePrime(strm: ZStream, bits: int, value: int): Promise<ReturnStatus>--><!--Device-Zip-inflatePrime(strm: ZStream, bits: int, value: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| bits | number | 是 | 指定要写入比特缓冲区的比特数。 |
| value | number | 是 | 用于填充比特缓冲区的比特值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

重置指定解压缩流的状态，使其恢复到初始化状态以重新开始新的解压操作。不会释放或重新分配内部缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateReset(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateReset(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

重置指定解压缩流的状态并更新窗口大小配置，以重新开始新的解压操作。不会释放或重新分配内部缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateReset2(strm: ZStream, windowBits: int): Promise<ReturnStatus>--><!--Device-Zip-inflateReset2(strm: ZStream, windowBits: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| windowBits | number | 是 | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

重置解压缩流的状态，以保留分配的霍夫曼解码树和预设字典。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateResetKeep(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateResetKeep(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

使用给定的字典数据初始化当前解压缩流的字典内容。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>--><!--Device-Zip-inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| dictionary | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 字典数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../../apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**示例：**

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

跳过无效的压缩数据，直到找到一个可能的完整刷新点为止。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateSync(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateSync(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800005](../../apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

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

查找当前解压缩流的同步点。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateSyncPoint(strm: ZStream): Promise<ReturnStatus>--><!--Device-Zip-inflateSyncPoint(strm: ZStream): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

验证压缩流结构内部的校验和。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-inflateValidate(strm: ZStream, check: int): Promise<ReturnStatus>--><!--Device-Zip-inflateValidate(strm: ZStream, check: int): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strm | [ZStream](arkts-basicservices-zlib-zstream-i.md) | 是 | 参考[ZStream定义](arkts-basicservices-zlib-zstream-i.md)。 |
| check | number | 是 | 预期的校验和。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReturnStatus> | Promise对象。返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

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

将压缩后的数据解压缩为原始的未压缩形式。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<ZipOutputInfo>--><!--Device-Zip-uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<ZipOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dest | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 目标缓冲区。 |
| source | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 源数据缓冲区。 |
| sourceLen | number | 否 | 源数据长度。默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ZipOutputInfo> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800005](../../apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

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

将压缩后的数据解压缩为原始的未压缩形式。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<DecompressionOutputInfo>--><!--Device-Zip-uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise<DecompressionOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dest | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 目标缓冲区。 |
| source | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 源数据缓冲区。 |
| sourceLen | number | 否 | 源数据长度。默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DecompressionOutputInfo> | Promise对象。返回结果状态、目标缓冲区的总大小和源数据长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800005](../../apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误) | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| [17800007](../../apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误) | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

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

返回指示编译时选项的标志。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-zlibCompileFlags(): Promise<int>--><!--Device-Zip-zlibCompileFlags(): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回指示编译时选项的标志。 |

**示例：**

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

获取当前链接的zlib库的版本信息。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Zip-zlibVersion(): Promise<string>--><!--Device-Zip-zlibVersion(): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象。返回当前zlib库的版本信息。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibVersion().then((data) => {
  console.info('zlibVersion success')
})

```

