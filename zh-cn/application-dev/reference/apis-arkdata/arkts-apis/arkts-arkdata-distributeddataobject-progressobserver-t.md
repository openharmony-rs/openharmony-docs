# ProgressObserver

```TypeScript
type ProgressObserver = (sessionId: string, progress: number) => void
```

定义传输进度的监听回调函数。

**起始版本：** 20

<!--Device-distributedDataObject-type ProgressObserver = (sessionId: string, progress: int) => void--><!--Device-distributedDataObject-type ProgressObserver = (sessionId: string, progress: int) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 标识变更对象的sessionId。长度不大于128字节，且只能包含字母、数字或下划线_。  |
| progress | number | 是 | 标识资产传输进度。取值范围为[-1, 100]，取值为整数，-1表示获取进度失败，100表示传输完成。  |

