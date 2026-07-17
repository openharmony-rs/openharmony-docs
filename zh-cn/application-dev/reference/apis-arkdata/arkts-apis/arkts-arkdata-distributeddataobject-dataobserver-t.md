# DataObserver

```TypeScript
type DataObserver = (sessionId: string, fields: Array<string>) => void
```

定义获取分布式对象数据变更的监听回调函数。

**起始版本：** 20

<!--Device-distributedDataObject-type DataObserver = (sessionId: string, fields: Array<string>) => void--><!--Device-distributedDataObject-type DataObserver = (sessionId: string, fields: Array<string>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 标识变更对象的sessionId。长度不大于128字节，且只能包含字母、数字或下划线_。 |
| fields | Array&lt;string&gt; | 是 | 标识对象变更的属性名。属性名可自定义，要求字符串非空且长度不超过128字节。 |

