# GZip

Gzip相关接口。

**起始版本：** 12

<!--Device-zlib-interface GZip--><!--Device-zlib-interface GZip-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

<a id="gzbuffer"></a>
## gzbuffer

```TypeScript
gzbuffer(size: number): Promise<number>
```

为当前库函数设置内部缓冲区尺寸。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzbuffer(size: long): Promise<int>--><!--Device-GZip-gzbuffer(size: long): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 需要设置的内部缓冲区尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，成功时，返回0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { fileIo as fs } from '@kit.CoreFileKit';
import { zlib } from '@kit.BasicServicesKit';

async function gzbufferDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzbuffer");
  let path = pathDir + "/gzbuffer/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzbuffer(648);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzbufferDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzclearerr"></a>
## gzclearerr

```TypeScript
gzclearerr(): Promise<void>
```

清除文件的错误和文件结束标志。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzclearerr(): Promise<void>--><!--Device-GZip-gzclearerr(): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclearerrDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclearerr");
  let path = pathDir + "/gzclearerr/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let writeNum = await gzip.gzwrite(writeBufferWithData, 16)
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBufferWithData = new ArrayBuffer(20);
  let readNum = await gzip.gzread(readBufferWithData);
  let eofNum = await gzip.gzeof();
  await gzip.gzclearerr();
  let eofNumClear = await gzip.gzeof();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzclearerrDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzclose"></a>
## gzclose

```TypeScript
gzclose(): Promise<ReturnStatus>
```

清除文件的所有挂起输出，如有必要，关闭文件和释放（解）压缩状态。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzclose(): Promise<ReturnStatus>--><!--Device-GZip-gzclose(): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800006](../../apis-basic-services-kit/errorcode-zlib.md#17800006-内存分配失败错误) | Memory allocation failed. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloseDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclose");
  let path = pathDir + "/gzclose/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzcloseDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzcloser"></a>
## gzcloser

```TypeScript
gzcloser(): Promise<ReturnStatus>
```

与gzclose()功能相同，仅适用于读取时。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzcloser(): Promise<ReturnStatus>--><!--Device-GZip-gzcloser(): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloserDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzcloser");
  let path = pathDir + "/gzcloser/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  await gzip.gzcloser();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzcloserDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzclosew"></a>
## gzclosew

```TypeScript
gzclosew(): Promise<ReturnStatus>
```

与gzclose()功能相同，仅适用于写入或追加时。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzclosew(): Promise<ReturnStatus>--><!--Device-GZip-gzclosew(): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800006](../../apis-basic-services-kit/errorcode-zlib.md#17800006-内存分配失败错误) | Memory allocation failed. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclosewDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclosew");
  let path = pathDir + "/gzclosew/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclosew();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzclosewDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzdirect"></a>
## gzdirect

```TypeScript
gzdirect(): Promise<number>
```

检查指定的gzip文件句柄文件是否直接访问原始未压缩数据，重新分配缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzdirect(): Promise<int>--><!--Device-GZip-gzdirect(): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，如果直接访问原始未压缩数据，则返回1。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdirectDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzdirect");
  let path = pathDir + "/gzdirect/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let directNum = await gzip.gzdirect();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzdirectDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzdopen"></a>
## gzdopen

```TypeScript
gzdopen(fd: number, mode: string): Promise<void>
```

将gzFile与文件描述符fd相关联，打开文件，用于进行读取并解压缩，或者压缩并写入。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzdopen(fd: int, mode: string): Promise<void>--><!--Device-GZip-gzdopen(fd: int, mode: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。通常情况下，通过系统调用“open”或其他方法获得的。 |
| mode | string | 是 | 用于指定访问模式。详情与[gzopen](arkts-basicservices-zlib-gzip-i.md#gzopen-1)一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800002](../../apis-basic-services-kit/errorcode-zlib.md#17800002-传入的文件或访问模式错误) | No such file or access mode error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdopenDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzdopen");
  let path = pathDir + "/gzdopen/test.gz";
  let file = fs.openSync(path, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  let gzip = zlib.createGZipSync();
  await gzip.gzdopen(file.fd, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzdopenDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzeof"></a>
## gzeof

```TypeScript
gzeof(): Promise<number>
```

检查gzip压缩文件的读取位置是否已到达文件的末尾。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzeof(): Promise<int>--><!--Device-GZip-gzeof(): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，如果在读取时设置了文件的文件结束指示符，则返回1。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzeofDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzeof");
  let path = pathDir + "/gzeof/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let writeNum = await gzip.gzwrite(writeBufferWithData, 16)
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBufferWithData = new ArrayBuffer(20);
  let readNum = await gzip.gzread(readBufferWithData);
  let eofNum = await gzip.gzeof();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzeofDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzerror"></a>
## gzerror

```TypeScript
gzerror(): Promise<GzErrorOutputInfo>
```

文件上发生的最后一个错误的错误消息。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzerror(): Promise<GzErrorOutputInfo>--><!--Device-GZip-gzerror(): Promise<GzErrorOutputInfo>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GzErrorOutputInfo&gt; | Promise对象，返回结果状态和出现的最后一个状态的状态消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzerrorDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzerror");
  let path = pathDir + "/gzerror/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  try {
    await gzip.gzwrite(writeBufferWithData, -1);
  } catch (errData) {
    await gzip.gzerror().then((GzErrorOutputInfo) => {
      console.info('errCode', GzErrorOutputInfo.status);
      console.info('errMsg', GzErrorOutputInfo.statusMsg);
    })
  }
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzerrorDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzflush"></a>
## gzflush

```TypeScript
gzflush(flush: CompressFlushMode): Promise<ReturnStatus>
```

将所有挂起的输出刷新到文件中。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzflush(flush: CompressFlushMode): Promise<ReturnStatus>--><!--Device-GZip-gzflush(flush: CompressFlushMode): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flush | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | 是 | 控制刷新操作的行为，参考[CompressFlushMode枚举](arkts-basicservices-zlib-compressflushmode-e.md)的定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzflushDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzflush");
  let path = pathDir + "/gzflush/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let flushNum = await gzip.gzflush(zlib.CompressFlushMode.NO_FLUSH);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzflushDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzfread"></a>
## gzfread

```TypeScript
gzfread(buf: ArrayBuffer, size: number, nitems: number): Promise<number>
```

从gzip压缩文件中解压缩并读取数据。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzfread(buf: ArrayBuffer, size: long, nitems: long): Promise<long>--><!--Device-GZip-gzfread(buf: ArrayBuffer, size: long, nitems: long): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 用于存储读取结果的目标缓冲区。 |
| size | number | 是 | 单个数据块中的字节数。 |
| nitems | number | 是 | 要写入的数据块数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回读取大小为size的完整数据块的数目。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfreadDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzfread");
  let path = pathDir + "/gzfread/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBuffer = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBuffer);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  await gzip.gzfwrite(writeBuffer, 8, 2);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBuffer = new ArrayBuffer(16);
  let result = await gzip.gzfread(readBuffer, 8, 2);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzfreadDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzfwrite"></a>
## gzfwrite

```TypeScript
gzfwrite(buf: ArrayBuffer, size: number, nitems: number): Promise<number>
```

将大小为size，数量为nitems的数据块从buf压缩并写入文件。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzfwrite(buf: ArrayBuffer, size: long, nitems: long): Promise<long>--><!--Device-GZip-gzfwrite(buf: ArrayBuffer, size: long, nitems: long): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 要将数据写入的缓冲区。 |
| size | number | 是 | 单个数据块中的字节数。 |
| nitems | number | 是 | 要写入的数据块数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回写入大小为size的完整数据块的数目。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfwriteDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzfwrite");
  let path = pathDir + "/gzfwrite/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let bufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(bufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let result = await gzip.gzfwrite(bufferWithData, 8, 2)
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzfwriteDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzgetc"></a>
## gzgetc

```TypeScript
gzgetc(): Promise<number>
```

从文件中读取并解压缩一个字节。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzgetc(): Promise<int>--><!--Device-GZip-gzgetc(): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回读取字符的ASCII值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzgetc");
  let path = pathDir + "/gzgetc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzputc(1);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzgetc();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzgetcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzgets"></a>
## gzgets

```TypeScript
gzgets(buf: ArrayBuffer): Promise<string>
```

从文件中读取字节并将其解压缩到buf中，直到读取len-1字符，或者直到读取换行符并将其传输到buf，或者遇到文件结束条件。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzgets(buf: ArrayBuffer): Promise<string>--><!--Device-GZip-gzgets(buf: ArrayBuffer): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 存储读取的行数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回以null结尾的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzgets");
  let path = pathDir + "/gzgets/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzputs("hello");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let bufferWithData = new ArrayBuffer(16);
  let result = await gzip.gzgets(bufferWithData);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzgetsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzoffset"></a>
## gzoffset

```TypeScript
gzoffset(): Promise<number>
```

返回文件的当前压缩（实际）读或写偏移量。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzoffset(): Promise<long>--><!--Device-GZip-gzoffset(): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回文件的当前压缩（实际）读或写偏移量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzoffsetDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzoffset");
  let path = pathDir + "/gzoffset/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzoffset();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzoffsetDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzopen"></a>
## gzopen

```TypeScript
gzopen(path: string, mode: string): Promise<void>
```

打开位于指定路径的gzip(.gz)文件，用于进行读取并解压缩，或者压缩并写入。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzopen(path: string, mode: string): Promise<void>--><!--Device-GZip-gzopen(path: string, mode: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要打开的文件路径。 |
| mode | string | 是 | 指定文件打开方法。<br>基础模式（必须三选一）：<br/>-?“r”或“rb”：读取模式，自动检测并解压gzip文件（若非gzip格式则直接读取原始数据）。<br/>-?“w”或“wb”：写入模式，创建新文件并压缩数据。<br/>-?“a”或“ab”：追加模式，在现有文件末尾追加新的gzip流（不校验原文件格式）。<br/>可选功能参数（可组合使用）：<br/>-?压缩级别：0（不压缩）至9（最佳压缩），默认压缩级别为6，需要配合写入模式或者追加模式使用。<br/>-?压缩策略：“f”（过滤策略）、“h”（霍夫曼策略）、“R”（游标编码策略）、“F”（固定编码策略），只能选取一种压缩策略。<br/>- 透明模式：“T”，写入时不压缩且不生成gzip头（生成普通文件），与压缩策略互斥。<br/>-?独占创建：“x”，如果文件存在则打开失败，需要配合写入模式或者追加模式使用<br/>-?close-on-exec标志：“e”，设置文件描述符的FD_CLOEXEC属性（依赖系统支持）。<br/>模式字符串示例：<br/>-?“r”：读取模式，读取时以二进制形式读取。<br/>-?“rb”：读取模式，读取时以二进制形式读取。<br/>-“wb6”：写入模式，压缩时以二进制形式写入，压缩级别为6。<br/>-?“wb9f”：写入模式，压缩时以二进制形式写入，压缩级别为最佳压缩，压缩策略采用过滤策略。<br/>-?“wbT”：写入模式，不压缩，生成普通文件。<br/>-?“wbx”：写入模式，压缩时以二进制形式写入，采用独占创建的方式写入文件。<br/>-?“abx”：追加模式，压缩时以二进制形式追加并写入，采用独占创建的方式写入文件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800002](../../apis-basic-services-kit/errorcode-zlib.md#17800002-传入的文件或访问模式错误) | No such file or access mode error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzopenDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzopen");
  let path = pathDir + "/gzopen/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzopenDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzprintf"></a>
## gzprintf

```TypeScript
gzprintf(format: string, ...args: Array<string | number>): Promise<number>
```

在字符串格式的控制下，将参数转换和格式化后，压缩并写入文件，如fprintf中所示。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzprintf(format: string, ...args: Array<string | double>): Promise<int>--><!--Device-GZip-gzprintf(format: string, ...args: Array<string | double>): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 格式化描述符和纯文本。 |
| args | Array&lt;string \| number&gt; | 是 | 可变参数列表。传入可变参数，例如gzprintf("name is %s, age is %d", "Tom", 23)，写入内容为“name is Tom, age is 23”。不传可变参数，例如gzprintf("name is %s, age is %d")，写入内容为“name is %s, age is %d”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回实际写入的未压缩字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzprintfDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzprintf");
  let path = pathDir + "/gzprintf/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzprintf("name is %s, age is %d", "Tom", 23);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzprintfDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzputc"></a>
## gzputc

```TypeScript
gzputc(ch: number): Promise<number>
```

将转换为无符号字符的c压缩并写入文件。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzputc(ch: int): Promise<int>--><!--Device-GZip-gzputc(ch: int): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | number | 是 | 写入字符ASCII。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回已写入的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzputc");
  let path = pathDir + "/gzputc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputc(0);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzputcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzputs"></a>
## gzputs

```TypeScript
gzputs(str: string): Promise<number>
```

压缩给定的以null结尾的字符串并将其写入文件，不包括终止的null字符。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzputs(str: string): Promise<int>--><!--Device-GZip-gzputs(str: string): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| str | string | 是 | 格式化描述符和纯文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回写入的字符数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzputs");
  let path = pathDir + "/gzputs/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputs("hello");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzputsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzread"></a>
## gzread

```TypeScript
gzread(buf: ArrayBuffer): Promise<number>
```

从文件中读取最多len个未压缩字节并将其解压缩到buf中。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzread(buf: ArrayBuffer): Promise<long>--><!--Device-GZip-gzread(buf: ArrayBuffer): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 目标偏移位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回实际读取的未压缩字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzreadDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzread");
  let path = pathDir + "/gzread/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBuffer = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBuffer);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  await gzip.gzwrite(writeBuffer, 16);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBuffer = new ArrayBuffer(16);
  let result = await gzip.gzread(readBuffer);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzreadDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzrewind"></a>
## gzrewind

```TypeScript
gzrewind(): Promise<ReturnStatus>
```

将文件指针重新定位到文件的开头，此功能仅用于读取。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzrewind(): Promise<ReturnStatus>--><!--Device-GZip-gzrewind(): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzrewindDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzrewind");
  let path = pathDir + "/gzrewind/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzrewind();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzrewindDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzseek"></a>
## gzseek

```TypeScript
gzseek(offset: number, whence: OffsetReferencePoint): Promise<number>
```

将起始位置设置为相对于文件中下一个gzread或gzwrite的偏移位置。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzseek(offset: long, whence: OffsetReferencePoint): Promise<long>--><!--Device-GZip-gzseek(offset: long, whence: OffsetReferencePoint): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 目标偏移位置。 |
| whence | [OffsetReferencePoint](arkts-basicservices-zlib-offsetreferencepoint-e.md) | 是 | 定义偏移的参考点，参考[OffsetReferencePoint枚举定义](arkts-basicservices-zlib-offsetreferencepoint-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回从未压缩流开始以字节为单位测量的结果偏移位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzseekDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzseek");
  let path = pathDir + "/gzseek/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzseek(2, zlib.OffsetReferencePoint.SEEK_CUR);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzseekDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzsetparams"></a>
## gzsetparams

```TypeScript
gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>
```

动态更新文件的压缩级别和压缩策略。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>--><!--Device-GZip-gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise<ReturnStatus>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 是 | 压缩级别，参考[CompressLevel枚举定义](arkts-basicservices-zlib-compresslevel-e.md)。 |
| strategy | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | 是 | 压缩策略，参考[CompressStrategy枚举定义](arkts-basicservices-zlib-compressstrategy-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ReturnStatus&gt; | Promise对象，返回结果状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800004](../../apis-basic-services-kit/errorcode-zlib.md#17800004-压缩流或解压流错误) | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzsetparamsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzsetparams");
  let path = pathDir + "/gzsetparams/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzsetparams(zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
    zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzsetparamsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gztell"></a>
## gztell

```TypeScript
gztell(): Promise<number>
```

返回文件中下一个gzread或gzwrite的起始位置。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gztell(): Promise<long>--><!--Device-GZip-gztell(): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回文件种下一个gzread或gzwrite的起始位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gztellDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gztell");
  let path = pathDir + "/gztell/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gztell();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gztellDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzungetc"></a>
## gzungetc

```TypeScript
gzungetc(c: number): Promise<number>
```

将c推回到流中，以便在下次读取文件时将作为第一个字符读取。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzungetc(c: int): Promise<int>--><!--Device-GZip-gzungetc(c: int): Promise<int>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| c | number | 是 | 回退到输入流之前的字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回推送的字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzungetcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzungetc");
  let path = pathDir + "/gzungetc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  await gzip.gzread(new ArrayBuffer(1));
  let result = await gzip.gzungetc(1);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzungetcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="gzwrite"></a>
## gzwrite

```TypeScript
gzwrite(buf: ArrayBuffer, len: number): Promise<number>
```

将buf中的len长度的未压缩字节进行压缩并将其写入文件。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GZip-gzwrite(buf: ArrayBuffer, len: long): Promise<long>--><!--Device-GZip-gzwrite(buf: ArrayBuffer, len: long): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 对象指向要写入的数据缓冲区。 |
| len | number | 是 | 未压缩字节长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回写入的未压缩字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [17800009](../../apis-basic-services-kit/errorcode-zlib.md#17800009-内部结构错误) | Internal structure error. |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzwriteDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzwrite");
  let path = pathDir + "/gzwrite/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let bufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(bufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let result = await gzip.gzwrite(bufferWithData, 16);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzwriteDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

