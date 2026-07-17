# hash

## hash

```TypeScript
declare function hash(path: string, algorithm: string): Promise<string>
```

计算文件的哈希值，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [hash:hash](arkts-file-hash.md)

<!--Device-unnamed-declare function hash(path: string, algorithm: string): Promise<string>--><!--Device-unnamed-declare function hash(path: string, algorithm: string): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待计算哈希值文件的应用沙箱路径。 |
| algorithm | string | 是 | 哈希计算采用的算法。可选?"md5"、"sha1"?或?"sha256"。建议采用安全强度更高的?"sha256"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象。返回文件的哈希值。表示为十六进制数字串，所有字母均大写。 |


## hash

```TypeScript
declare function hash(path: string, algorithm: string, callback: AsyncCallback<string>): void
```

计算文件的哈希值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [hash:hash](arkts-file-hash.md)

<!--Device-unnamed-declare function hash(path: string, algorithm: string, callback: AsyncCallback<string>): void--><!--Device-unnamed-declare function hash(path: string, algorithm: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待计算哈希值文件的应用沙箱路径。 |
| algorithm | string | 是 | 哈希计算采用的算法。可选?"md5"、"sha1"?或?"sha256"。建议采用安全强度更高的?"sha256"。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 异步计算文件哈希操作之后的回调函数（其中给定文件哈希值表示为十六进制数字串，所有字母均大写）。 |

