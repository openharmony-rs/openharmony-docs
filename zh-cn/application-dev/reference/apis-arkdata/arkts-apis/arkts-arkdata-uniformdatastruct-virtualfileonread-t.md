# VirtualFileOnRead

```TypeScript
type VirtualFileOnRead = (id: string, offset: number, length: number) => Promise<Uint8Array>
```

从虚拟文件读取至多 length 字节的回调，单次请求最大为 5 MiB。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformDataStruct-type VirtualFileOnRead = (id: string, offset: long, length: int) => Promise<Uint8Array>--><!--Device-uniformDataStruct-type VirtualFileOnRead = (id: string, offset: long, length: int) => Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 虚拟文件标识。 |
| offset | number | 是 | 从 0 开始计算的读取字节偏移。 |
| length | number | 是 | 本次最多读取的字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 通过 Promise 返回的文件内容，空数组表示文件结束。 |
