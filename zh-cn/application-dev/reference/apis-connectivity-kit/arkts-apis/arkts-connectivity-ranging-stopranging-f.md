# stopRanging

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## stopRanging

```TypeScript
function stopRanging(callback: Callback<RangingResult>, params?: RangingParams): void
```

停止正在进行中的主动测距。

需与[startRanging](arkts-connectivity-ranging-startranging-f.md)配合使用，传入的callback必须与启动测距时的callback为同一引用对象。

此方法同时释放测距占用的资源。为实现正确的资源管理，[startRanging](arkts-connectivity-ranging-startranging-f.md)测距启动后必须调用stopRanging停止测距，避免测距资源泄漏。

测距状态的变化通过[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)回调进行通知。

如果未调用过[startRanging](arkts-connectivity-ranging-startranging-f.md)直接调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)将抛出设备未发起测距错误34900 050。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingResult](arkts-connectivity-ranging-rangingresult-i.md)&gt; | 是 | 测距结果回调，需与[startRanging](arkts-connectivity-ranging-startranging-f.md)传入的callback为同一引用对象，否则将无法停止已启动的测距。该入参要求与[startRanging](arkts-connectivity-ranging-startranging-f.md)中的callback要求相同。 |
| params | [RangingParams](arkts-connectivity-ranging-rangingparams-i.md) | 否 | 测距参数，包含deviceId和测距能力类型，与[startRanging](arkts-connectivity-ranging-startranging-f.md)接口中的params相同。默认值：undefined。指定此参数时仅停止与指定目标设备的测距；不传入此参数时停止与callback关联的所有设备的测距。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900050](../errorcode-fusionConnectivity.md#34900050-该设备未发起测距) | The device has not initiated ranging. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-不支持指定类型的测距服务) | The specified type of ranging service is not supported. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-参数不符合业务规格) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
