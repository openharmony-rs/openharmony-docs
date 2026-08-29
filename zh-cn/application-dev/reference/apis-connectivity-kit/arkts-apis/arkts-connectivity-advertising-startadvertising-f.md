# startAdvertising

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams): Promise<number>
```

发送星闪广播。使用Promise异步回调。适用于设备发现、设备信息广播等需要将本端设备能力或数据对外发布的业务场景，配合 [advertising.onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md)可监听广播启停状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md) | 是 | 广播相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回本次开启的广播ID。广播ID是随机分配的唯一标识值，范围[0, 255]，与 [advertising.stopAdvertising]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-整数超出范围) | Integer out of range. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
