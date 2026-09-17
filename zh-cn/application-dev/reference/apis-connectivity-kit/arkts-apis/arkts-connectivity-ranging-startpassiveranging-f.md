# startPassiveRanging

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## startPassiveRanging

```TypeScript
function startPassiveRanging(capabilityType: RangingTypes): Promise<number>
```

启动被动测距模式。本端设备将作为测距信标广播测距数据包，允许其他支持对应测距类型的主动测距设备发现本端设备。典型应用场景包括：本端设备作为被定位标签或防丢贴片、固定信标部署等，适用于本端需要被其他设备测量距离的场景。

使用测距接口前，需先通过[getRangingCapability](arkts-connectivity-ranging-getrangingcapability-f.md)确认设备支持对应的测距类型。

使用星闪HADM测距时，本端设备在发起被动测距后，无法使用主动测距模式。如需使用主动测距，需先调用[stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md)停止被动测距。

同一测距能力类型仅支持单次调用[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)，成功后返回的handle对应独立的广播会话。

如需对同一测距能力再次调用[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)，需要先调用[stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md)结束本次的被动测距，如果直接再次调用，接口将返回错误码34900099。

如果启动测距时，对应类型的测距服务已下线，那么调用本接口时会抛出服务未使能错误码34900053。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilityType | [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md) | 是 | 测距能力类型。参数必须要填入有效值，否则接口会抛出34900052错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回被动测距会话的句柄标识符handle，数值范围[0, 2147483647)。该句柄用于：1. 在[stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md)中指定要停止的被动测距会话。 2. 在[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)回调的[stateInfo.handle](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)中标识对应的被动测距 会话。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-不支持指定类型的测距服务) | The specified type of ranging service is not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-测距服务关闭) | The ranging service is disabled. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
