# VirtualFileOnCancel

```TypeScript
type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>
```

取消指定虚拟文件待处理任务的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformDataStruct-type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>--><!--Device-uniformDataStruct-type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| idList | Array&lt;string&gt; | 是 | 需要取消的虚拟文件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 用于返回结果的 Promise。 |
