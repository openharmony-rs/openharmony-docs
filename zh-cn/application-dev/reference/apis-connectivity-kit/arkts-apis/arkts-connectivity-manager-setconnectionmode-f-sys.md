# setConnectionMode（系统接口）

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## setConnectionMode

```TypeScript
function setConnectionMode(mode: ConnectionMode, duration: number): Promise<void>
```

设置连接模式。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | 是 | 表示要设置的连接模式。 |
| duration | number | 是 | 表示设置模式的持续时间，单位为s，取值范围为大于等于0的整数，若为0则表示无限制。 取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-整数超出范围) | Integer out of range. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
