# VirtualFileOnStat

```TypeScript
type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>
```

获取虚拟文件元数据的回调，不能替代起拖前声明文件大小。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformDataStruct-type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>--><!--Device-uniformDataStruct-type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 虚拟文件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VirtualFileItem](arkts-arkdata-uniformdatastruct-virtualfileitem-i.md)&gt; | 通过 Promise 返回的虚拟文件元数据，必须包含非负的 size。 |
