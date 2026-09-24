# createA2dpSnkProfile

## 导入模块

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## createA2dpSnkProfile

```TypeScript
function createA2dpSnkProfile(): A2dpSinkProfile
```

创建a2dp sink实例。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [A2dpSinkProfile](arkts-connectivity-a2dp-a2dpsinkprofile-i-sys.md) | 返回profile的实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
