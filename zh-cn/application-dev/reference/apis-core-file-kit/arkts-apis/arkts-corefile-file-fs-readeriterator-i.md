# ReaderIterator

文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-unnamed-declare interface ReaderIterator--><!--Device-unnamed-declare interface ReaderIterator-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## next

```TypeScript
next(): ReaderIteratorResult
```

获取迭代器下一项内容。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-ReaderIterator-next(): ReaderIteratorResult--><!--Device-ReaderIterator-next(): ReaderIteratorResult-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 文件读取迭代器返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900037 | No data available |
| 13900042 | Unknown error |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Options } from '@kit.CoreFileKit';

let filePath = pathDir + "/test.txt";
let options: Options = {
  encoding: 'utf-8'
};
fileIo.readLines(filePath, options).then((readerIterator: fileIo.ReaderIterator) => {
  for (let it = readerIterator.next(); !it.done; it = readerIterator.next()) {
    console.info(`Succeeded in reading lines, content: ${it.value}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to read lines. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Options } from '@kit.CoreFileKit';

let filePath = pathDir + "/test.txt";
let options: Options = {
  encoding: 'utf-8'
};
fileIo.readLines(filePath, options).then((readerIterator:fileIo.ReaderIterator) => {
  for (let it = readerIterator.next(); !it.done; it = readerIterator.next()) {
    console.info(`Succeeded in reading lines, content: ${it.value}`);
  }
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to read lines. Code: ${err.code}, message: ${err.message}`);
});
```

