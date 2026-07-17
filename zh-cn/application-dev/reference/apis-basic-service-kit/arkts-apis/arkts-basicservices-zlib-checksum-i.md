# Checksum

校验对象。

**起始版本：** 12

<!--Device-zlib-interface Checksum--><!--Device-zlib-interface Checksum-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## adler32

```TypeScript
adler32(adler: number, buf: ArrayBuffer): Promise<number>
```

计算Adler-32校验和。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-adler32(adler: long, buf: ArrayBuffer): Promise<long>--><!--Device-Checksum-adler32(adler: long, buf: ArrayBuffer): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adler | number | 是 | Adler-32校验和的初始值。 |
| buf | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 计算校验和数据缓冲区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回计算后的Adler-32校验和。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.adler32(0, arrayBufferIn).then(data => {
  console.info('adler32 success', data);
})

```

## adler32Combine

```TypeScript
adler32Combine(adler1: number, adler2: number, len2: number): Promise<number>
```

将两个Adler-32校验和合并。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-adler32Combine(adler1: long, adler2: long, len2: long): Promise<long>--><!--Device-Checksum-adler32Combine(adler1: long, adler2: long, len2: long): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adler1 | number | 是 | 第一个要合并的Adler-32校验和。 |
| adler2 | number | 是 | 第二个要合并的Adler-32校验和。 |
| len2 | number | 是 | 第二个Adler-32校验和的数据块的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回合并后的Adler-32校验和。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(12);
  let data = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    data[i] = str.charCodeAt(i);
  }
  let checksum = zlib.createChecksumSync()
  let adler1 = 0;
  let adler2 = 1;
  await checksum.adler32(0, arrayBufferIn).then(data => {
    console.info('adler32 success', data);
    adler1 = data;
  })
  await checksum.adler32(1, arrayBufferIn).then(data => {
    console.info('adler32 success', data);
    adler2 = data;
  })
  await checksum.adler32Combine(adler1, adler2, 12).then((data) => {
    console.info('adler32Combine success', data);
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}

```

## crc32

```TypeScript
crc32(crc: number, buf: ArrayBuffer): Promise<number>
```

更新CRC-32校验。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-crc32(crc: long, buf: ArrayBuffer): Promise<long>--><!--Device-Checksum-crc32(crc: long, buf: ArrayBuffer): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| crc | number | 是 | CRC-32校验的初始值。 |
| buf | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 计算校验数据缓冲区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回更新后的CRC-32校验。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc32(0, arrayBufferIn).then((data) => {
  console.info('crc32 success', data);
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})

```

## crc32Combine

```TypeScript
crc32Combine(crc1: number, crc2: number, len2: number): Promise<number>
```

将两个CRC-32校验合并。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-crc32Combine(crc1: long, crc2: long, len2: long): Promise<long>--><!--Device-Checksum-crc32Combine(crc1: long, crc2: long, len2: long): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| crc1 | number | 是 | 第一个要合并的CRC-32校验。 |
| crc2 | number | 是 | 第二个要合并的CRC-32校验。 |
| len2 | number | 是 | 第二个CRC-32校验的数据块的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回合并后的CRC-32校验。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(12);
  let data = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    data[i] = str.charCodeAt(i);
  }
  let checksum = zlib.createChecksumSync()
  let crc1 = 0;
  let crc2 = 1;
  await checksum.crc32(0, arrayBufferIn).then(data => {
    console.info('crc32 success', data);
    crc1 = data;
  })
  await checksum.crc32(1, arrayBufferIn).then(data => {
    console.info('crc32 success', data);
    crc2 = data;
  })
  await checksum.crc32Combine(crc1, crc2, 12).then((data) => {
    console.info('crc32Combine success', data);
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}

```

## crc64

```TypeScript
crc64(crc: number, buf: ArrayBuffer): Promise<number>
```

更新CRC-64校验。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-crc64(crc: long, buf: ArrayBuffer): Promise<long>--><!--Device-Checksum-crc64(crc: long, buf: ArrayBuffer): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| crc | number | 是 | CRC-64校验的初始值。 |
| buf | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 计算校验数据缓冲区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回更新后的CRC-64校验。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc64(0, arrayBufferIn).then((data) => {
  console.info('crc64 success', data);
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})

```

## getCrc64Table

```TypeScript
getCrc64Table(): Promise<Array<number>>
```

输出CRC-64校验表。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-getCrc64Table(): Promise<Array<long>>--><!--Device-Checksum-getCrc64Table(): Promise<Array<long>>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | Promise对象。返回CRC-64校验表。 |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrc64Table().then((data) => {
  console.info('getCrc64Table success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})

```

## getCrcTable

```TypeScript
getCrcTable(): Promise<Array<number>>
```

输出CRC-32校验表。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Checksum-getCrcTable(): Promise<Array<long>>--><!--Device-Checksum-getCrcTable(): Promise<Array<long>>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | Promise对象。返回CRC-32校验表。 |

**示例：**

```TypeScript
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrcTable().then((data) => {
  console.info('getCrcTable success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})

```

