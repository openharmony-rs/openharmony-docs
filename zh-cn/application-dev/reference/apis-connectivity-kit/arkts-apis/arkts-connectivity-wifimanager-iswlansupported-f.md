# isWlanSupported

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isWlanSupported

```TypeScript
function isWlanSupported(): boolean
```

查询WLAN是否可用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function isWlanSupported(): boolean--><!--Device-wifiManager-function isWlanSupported(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WLAN是否可用。{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2401000](../errorcode-wifi.md#2401000-sta内部异常) | Operation failed. |

