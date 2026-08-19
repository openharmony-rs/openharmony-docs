# getAllCapabilityList

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## getAllCapabilityList

```TypeScript
function getAllCapabilityList(): Promise<Capability[]>
```

返回所有能力列表

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-carAwareness-function getAllCapabilityList(): Promise<Capability[]>--><!--Device-carAwareness-function getAllCapabilityList(): Promise<Capability[]>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Capability[]&gt; | Promise用于返回所有的能力列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Car awareness not supported. Function can not work correctly due to limited device capabilities. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-carAwareness.md#34000001-服务异常) | Service exception. |

