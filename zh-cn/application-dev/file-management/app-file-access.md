# 应用文件访问(ArkTS)

应用需要对应用文件目录下的应用文件进行查看、创建、读写、删除、移动、复制、获取属性等访问操作，下文介绍具体方法。

## 接口说明

开发者通过基础文件操作接口（[ohos.file.fs](../reference/apis-core-file-kit/js-apis-file-fs.md)）实现应用文件访问能力，主要功能如下表所示。

**表1** 基础文件操作接口功能，其中“√”表示支持，“-”表示不区分同步和异步。

| 接口名 | 功能 | 接口类型 | 支持同步 | 支持异步 |
| -------- | -------- | -------- | -------- | -------- |
| access | 检查文件是否存在 | 方法 | √ | √ |
| close | 关闭文件 | 方法 | √ | √ |
| copyFile | 复制文件 | 方法 | √ | √ |
| createStream | 基于文件路径打开文件流 | 方法 | √ | √ |
| listFile | 列出文件夹下所有文件名 | 方法 | √ | √ |
| mkdir | 创建目录 | 方法 | √ | √ |
| moveFile | 移动文件 | 方法 | √ | √ |
| open | 打开文件 | 方法 | √ | √ |
| read | 从文件读取数据 | 方法 | √ | √ |
| rename | 重命名文件或文件夹 | 方法 | √ | √ |
| rmdir | 删除整个目录 | 方法 | √ | √ |
| stat | 获取文件详细属性信息 | 方法 | √ | √ |
| unlink | 删除单个文件 | 方法 | √ | √ |
| write | 将数据写入文件 | 方法 | √ | √ |
| Stream.close | 关闭文件流 | 方法 | √ | √ |
| Stream.flush | 刷新文件流 | 方法 | √ | √ |
| Stream.write | 将数据写入流文件 | 方法 | √ | √ |
| Stream.read | 从流文件读取数据 | 方法 | √ | √ |
| File.fd | 获取文件描述符 | 属性 | - | - |
| OpenMode | 设置文件打开标签 | 属性 | - | - |
| Filter | 设置文件过滤配置项 | 类型 | - | - |

> **注意：**
>
> 使用基础文件操作接口时，耗时较长的操作，例如：read、write等，建议使用异步接口，避免应用崩溃。

## 开发示例

在对应用文件开始访问前，开发者需要[获取应用文件路径](../application-models/application-context-stage.md#获取应用文件路径)。以从UIAbilityContext获取HAP级别的文件路径为例进行说明，UIAbilityContext的获取方式请参见[获取UIAbility的上下文信息](../application-models/uiability-usage.md#获取uiability的上下文信息)。

下面介绍几种常用操作示例。

### 新建并读写一个文件

以下示例代码演示了如何新建一个文件并对其读写。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';
import { buffer } from '@kit.ArkTS';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

function createFile(context: common.UIAbilityContext): void {
  let filesDir = context.filesDir;
  // 文件不存在时创建并打开文件，文件存在时打开文件
  let file = fs.openSync(filesDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  // 写入一段内容至文件
  let writeLen = fs.writeSync(file.fd, "Try to write str.");
  console.info("The length of str is: " + writeLen);
  // 创建一个大小为1024字节的ArrayBuffer对象，用于存储从文件中读取的数据
  let arrayBuffer = new ArrayBuffer(1024);
  // 设置读取的偏移量和长度
  let readOptions: ReadOptions = {
    offset: 0,
    length: arrayBuffer.byteLength
  };
  // 读取文件内容到ArrayBuffer对象中，并返回实际读取的字节数
  let readLen = fs.readSync(file.fd, arrayBuffer, readOptions);
  // 将ArrayBuffer对象转换为Buffer对象，并转换为字符串输出
  let buf = buffer.from(arrayBuffer, 0, readLen);
  console.info("the content of file: " + buf.toString());
  // 关闭文件
  fs.closeSync(file);
}
```

### 读取文件内容并写入到另一个文件

以下示例代码演示了如何从一个文件读写内容到另一个文件。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions, WriteOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

function readWriteFile(context: common.UIAbilityContext): void {
  let filesDir = context.filesDir;
  // 打开文件
  let srcFile = fs.openSync(filesDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  let destFile = fs.openSync(filesDir + '/destFile.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  // 读取源文件内容并写入至目的文件
  let bufSize = 4096;
  let readSize = 0;
  let buf = new ArrayBuffer(bufSize);
  let readOptions: ReadOptions = {
    offset: readSize,
    length: bufSize
  };
  let readLen = fs.readSync(srcFile.fd, buf, readOptions);
  while (readLen > 0) {
    readSize += readLen;
    let writeOptions: WriteOptions = {
      length: readLen
    };
    fs.writeSync(destFile.fd, buf, writeOptions);
    readOptions.offset = readSize;
    readLen = fs.readSync(srcFile.fd, buf, readOptions);
  }
  // 关闭文件
  fs.closeSync(srcFile);
  fs.closeSync(destFile);
}
```

> **说明：**
>
> 使用读写接口时，需注意可选项参数offset的设置。对于已存在且读写过的文件，文件偏移指针默认在上次读写操作的终止位置。

### 以流的形式读写文件

以下示例代码演示了如何使用流接口读取test.txt的文件内容并写入到destFile.txt文件中。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

async function readWriteFileWithStream(context: common.UIAbilityContext): Promise<void> {
  let filesDir = context.filesDir;
  // 创建并打开输入文件流
  let inputStream = fs.createStreamSync(filesDir + '/test.txt', 'r+');
  // 创建并打开输出文件流
  let outputStream = fs.createStreamSync(filesDir + '/destFile.txt', "w+");

  let bufSize = 4096;
  let readSize = 0;
  let buf = new ArrayBuffer(bufSize);
  let readOptions: ReadOptions = {
    offset: readSize,
    length: bufSize
  };
  // 以流的形式读取源文件内容并写入到目标文件
  let readLen = await inputStream.read(buf, readOptions);
  readSize += readLen;
  while (readLen > 0) {
    const writeBuf = readLen < bufSize ? buf.slice(0, readLen) : buf;
    await outputStream.write(writeBuf);
    readOptions.offset = readSize;
    readLen = await inputStream.read(buf, readOptions);
    readSize += readLen;
  }
  // 关闭文件流
  inputStream.closeSync();
  outputStream.closeSync();
}
```

> **说明：**
>
> 使用流接口时，需注意流的及时关闭。同时流的异步接口应严格遵循异步接口使用规范，避免同步、异步接口混用。流接口不支持并发读写。

### 查看文件列表

以下示例代码演示了如何查看文件列表。

```ts
import { fileIo as fs, Filter, ListFileOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

// 查看文件列表
function getListFile(context: common.UIAbilityContext): void {
  let listFileOption: ListFileOptions = {
    recursion: false,
    listNum: 0,
    filter: {
      suffix: [".png", ".jpg", ".txt"],
      displayName: ["test*"],
      fileSizeOver: 0,
      lastModifiedAfter: new Date(0).getTime()
    }
  };
  let filesDir = context.filesDir;
  let files = fs.listFileSync(filesDir, listFileOption);
  for (let i = 0; i < files.length; i++) {
    console.info(`The name of file: ${files[i]}`);
  }
}
```

### 使用文件流

以下示例代码演示了如何使用文件可读流，文件可写流。

```ts
// pages/xxx.ets
import { fileIo as fs } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

function copyFileWithReadable(context: common.UIAbilityContext): void {
  let filesDir = context.filesDir;
  // 创建文件可读流
  const rs = fs.createReadStream(`${filesDir}/read.txt`);
  // 创建文件可写流
  const ws = fs.createWriteStream(`${filesDir}/write.txt`);
  // 暂停模式拷贝文件。在拷贝数据时，将原始数据暂停，然后将数据复制到另一个位置，适用于对数据完整性和一致性要求较高的场景
  rs.on('readable', () => {
    const data = rs.read();
    if (!data) {
      return;
    }
    ws.write(data);
  });
}

function copyFileWithData(context: common.UIAbilityContext): void {
  let filesDir = context.filesDir;
  // 创建文件可读流
  const rs = fs.createReadStream(`${filesDir}/read.txt`);
  // 创建文件可写流
  const ws = fs.createWriteStream(`${filesDir}/write.txt`);
  // 流动模式拷贝文件。数据的读取和写入是同时进行的，不需要暂停原始数据的访问，适用于对数据实时性要求较高的场景
  rs.on('data', (emitData) => {
    const data = emitData?.data;
    if (!data) {
      return;
    }
    ws.write(data as Uint8Array);
  });
}
```

### 使用文件哈希流

哈希流是一种数据传输和存储技术，可以将任意长度的数据转换为固定长度的哈希值来验证数据的完整性和一致性。以下代码演示了如何使用文件哈希处理接口（[ohos.file.hash](../reference/apis-core-file-kit/js-apis-file-hash.md)）来处理文件哈希流。

```ts
// pages/xxx.ets
import { fileIo as fs } from '@kit.CoreFileKit';
import { hash } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 获取应用文件路径，请在组件内获取context
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

function hashFileWithStream(context: common.UIAbilityContext) {
  let filesDir = context.filesDir;
  const filePath = `${filesDir}/test.txt`;
  // 创建文件可读流
  const rs = fs.createReadStream(filePath);
  // 创建哈希流
  const hs = hash.createHash('sha256');
  rs.on('data', (emitData) => {
    const data = emitData?.data;
    hs.update(new Uint8Array(data?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  });
  rs.on('close', async () => {
    const hashResult = hs.digest();
    const fileHash = await hash.hash(filePath, 'sha256');
    console.info(`hashResult: ${hashResult}, fileHash: ${fileHash}`);
  });
}

```