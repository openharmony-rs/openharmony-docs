# genSessionId

## 导入模块

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## genSessionId

```TypeScript
function genSessionId(): string
```

随机创建一个sessionId。

**起始版本：** 8

<!--Device-distributedDataObject-function genSessionId(): string--><!--Device-distributedDataObject-function genSessionId(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 随机创建的sessionId。 |

**示例：**

```TypeScript
let sessionId: string = distributedDataObject.genSessionId();

```

