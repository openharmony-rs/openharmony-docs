# genSessionId

## genSessionId

```TypeScript
function genSessionId(): string
```

随机创建一个sessionId。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-distributedDataObject-function genSessionId(): string--><!--Device-distributedDataObject-function genSessionId(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 随机创建的sessionId。 |

## 示例

```TypeScript
let sessionId: string = distributedDataObject.genSessionId();
```

