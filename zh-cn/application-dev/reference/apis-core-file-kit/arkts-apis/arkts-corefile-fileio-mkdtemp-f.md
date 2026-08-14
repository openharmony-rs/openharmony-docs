# mkdtemp

## mkdtemp

```TypeScript
declare function mkdtemp(prefix: string): Promise<string>
```

创建临时目录，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp)

<!--Device-unnamed-declare function mkdtemp(prefix: string): Promise<string>--><!--Device-unnamed-declare function mkdtemp(prefix: string): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 用随机产生的字符串替换以“XXXXXX”结尾目录路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回生成的唯一目录路径。 |


## mkdtemp

```TypeScript
declare function mkdtemp(prefix: string, callback: AsyncCallback<string>): void
```

创建临时目录，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp)

<!--Device-unnamed-declare function mkdtemp(prefix: string, callback: AsyncCallback<string>): void--><!--Device-unnamed-declare function mkdtemp(prefix: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 用随机产生的字符串替换以“XXXXXX”结尾目录路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 异步创建临时目录之后的回调。 |

