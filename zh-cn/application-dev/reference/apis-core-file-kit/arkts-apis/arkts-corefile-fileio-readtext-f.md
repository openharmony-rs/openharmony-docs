# readText

## 导入模块

```TypeScript
```

## readText

```TypeScript
declare function readText(
  filePath: string,
  options?: {
    position?: number;
    length?: number;
    encoding?: string;
  }
): Promise<string>
```

基于文本方式读取文件（即直接读取文件的文本内容），使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [readText](arkts-corefile-file-fs-readtext-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 待读取文件的应用沙箱路径。 |
| options | {     position?: number;     length?: number;     encoding?: string;   } | 否 | 支持如下选项：   - position，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。   - length，number 类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。  - encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'，仅支持 'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象。返回读取文件的内容。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
fileio.readText(filePath).then((str: string) => {
  console.info("readText succeed:" + str);
}).catch((err: BusinessError) => {
  console.error("readText failed with error:" + err);
});
```


## readText

```TypeScript
declare function readText(
  filePath: string,
  options: {
    position?: number;
    length?: number;
    encoding?: string;
  },
  callback: AsyncCallback<string>
): void
```

基于文本方式读取文件（即直接读取文件的文本内容），使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [readText](arkts-corefile-file-fs-readtext-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 待读取文件的应用沙箱路径。 |
| options | {     position?: number;     length?: number;     encoding?: string;   } | 是 | 支持如下选项：   - position，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。  - length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。  - encoding，string类型，表示数据的编码方式，默认 'utf-8'，仅支持 'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回读取文件的内容。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
class Option {
  length: number = 4096;
  position: number = 0;
  encoding: string = 'utf-8';
}
let option = new Option();
option.position = 1;
option.encoding = 'utf-8';
fileio.readText(filePath, option, (err: BusinessError, str: string) => {
  // do something
});
```
