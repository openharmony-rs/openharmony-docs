# stopPassiveRanging

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## stopPassiveRanging

```TypeScript
function stopPassiveRanging(handle: number, capabilityType: RangingTypes): void
```

停止被动测距模式。根据指定的句柄和测距类型停止对应的被动测距广播，并清理相关资源。

只有[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)接口调用成功之后，才需要调用本接口停止被动测距广播。如果未调用过[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)直接调用[stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md)，由于handle无效将抛出参数不符合规格错误34900054。为实现正确的资源管理，[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)启动被动测距后必须调用[stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md)停止被动测距，避免测距资源泄漏。

停止测距的状态变化通过[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)回调通知。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | 测距监控句柄，应为[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)返回的有效句柄，否则会抛出34900054错误；停止后该handle不再有效，不可重复使用。 |
| capabilityType | [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md) | 是 | 测距能力类型，参数需与[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)接口传入的capabilityType保持一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-不支持指定类型的测距服务) | The specified type of ranging service is not supported. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-参数不符合业务规格) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
