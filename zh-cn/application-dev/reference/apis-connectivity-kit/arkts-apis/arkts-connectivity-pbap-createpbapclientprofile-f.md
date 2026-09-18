# createPbapClientProfile

## 导入模块

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## createPbapClientProfile

```TypeScript
function createPbapClientProfile(): PbapClientProfile
```

创建PBAP客户端配置文件的实例。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PbapClientProfile](arkts-connectivity-pbap-pbapclientprofile-i-sys.md) | 返回pbap客户端配置文件的实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
