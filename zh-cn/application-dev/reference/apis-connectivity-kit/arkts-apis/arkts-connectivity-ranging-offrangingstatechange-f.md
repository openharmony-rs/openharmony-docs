# offRangingStateChange

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## offRangingStateChange

```TypeScript
function offRangingStateChange(callback?: Callback<RangingStateChangeInfo>): void
```

注销测距状态变化回调。

该接口只有在[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)之后调用才会有效。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingStateChangeInfo](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)&gt; | 否 | 测距状态回调。传入此参数时仅取消通过[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)接口使用相同入参已注册的回调，如果传入的callback未注册过，该接口不会处理；不传入此参数时接口会取消所有通过[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)接口已注册过的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
