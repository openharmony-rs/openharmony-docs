# stopScan

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

<a id="stopscan"></a>
## stopScan

```TypeScript
function stopScan(): Promise<void>
```

停止扫描。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-scan-function stopScan(): Promise<void>--><!--Device-scan-function stopScan(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | @throws { BusinessError } 201 - 权限被拒绝。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限被拒绝。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

