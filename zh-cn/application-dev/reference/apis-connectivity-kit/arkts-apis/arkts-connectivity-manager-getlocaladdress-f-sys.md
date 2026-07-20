# getLocalAddress（系统接口）

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

<a id="getlocaladdress"></a>
## getLocalAddress

```TypeScript
function getLocalAddress(): string
```

获取本端设备的MAC地址。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.GET_NEARLINK_LOCAL_MAC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-manager-function getLocalAddress(): string--><!--Device-manager-function getLocalAddress(): string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 本地MAC地址。例如，“11:22:33:AA:BB:FF”。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

