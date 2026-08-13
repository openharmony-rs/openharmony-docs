# readText

## readText

```TypeScript
function readText(
  filePath: string,
  options?: ReadTextOptions
): Promise<string>
```

基于文本方式读取文件（即直接读取文件的文本内容）。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function readText(  filePath: string,  options?: ReadTextOptions): Promise<string>--><!--Device-fileIo-function readText(  filePath: string,  options?: ReadTextOptions): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [ReadTextOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readtextoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。&lt;br/&gt;-  length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认文件长度。&lt;br/&gt;- encoding，string类型，当数据是 string 类型时有效，表示数据的编码方式，默认 'utf-8'， 仅支持'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回读取文件的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900019 | Is a directory |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900044 | Network is unreachable |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |


## readText

```TypeScript
function readText(filePath: string, callback: AsyncCallback<string>): void
```

基于文本方式读取文件内容。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function readText(filePath: string, callback: AsyncCallback<string>): void--><!--Device-fileIo-function readText(filePath: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回读取文件的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900019 | Is a directory |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |


## readText

```TypeScript
function readText(
  filePath: string,
  options: ReadTextOptions,
  callback: AsyncCallback<string>
): void
```

基于文本方式读取文件内容，支持配置读取选项。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function readText(  filePath: string,  options: ReadTextOptions,  callback: AsyncCallback<string>): void--><!--Device-fileIo-function readText(  filePath: string,  options: ReadTextOptions,  callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [ReadTextOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readtextoptions-i.md) | 是 | 支持如下选项：&lt;br/&gt;- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。&lt;br/&gt;-  length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认文件长度。&lt;br/&gt;- encoding，string类型，表示数据的编码方式，默认 'utf-8'，仅支持 'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回读取文件的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900019 | Is a directory |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

