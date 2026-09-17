# createOppServerProfile（系统接口）

## 导入模块

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## createOppServerProfile

```TypeScript
function createOppServerProfile(): OppServerProfile
```

创建oppServer profile实例。

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OppServerProfile](arkts-connectivity-opp-oppserverprofile-i-sys.md) | 返回profile实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
