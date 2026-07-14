# readText

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

**替代接口：** [fs:readText](arkts-corefile-file-fs-readtext-f.md#readtext-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 待读取文件的应用沙箱路径。 |
| options | {    position?: number;    length?: number;    encoding?: string;  } | 否 | 支持如下选项：<br/>-?position，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。<br/>-?length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?encoding，string类型，当数据是?string?类型时有效，表示数据的编码方式，默认?'utf-8'，仅支持?'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回读取文件的内容。 |


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

**替代接口：** [fs:readText](arkts-corefile-file-fs-readtext-f.md#readtext-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 待读取文件的应用沙箱路径。 |
| options | {    position?: number;    length?: number;    encoding?: string;  } | 是 | 支持如下选项：<br/>-?position，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。<br/>-?length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?encoding，string类型，表示数据的编码方式，默认?'utf-8'，仅支持?'utf-8'。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回读取文件的内容。 |

