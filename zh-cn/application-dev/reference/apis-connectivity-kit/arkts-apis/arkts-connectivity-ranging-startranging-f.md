# startRanging

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## startRanging

```TypeScript
function startRanging(params: RangingParams, callback: Callback<RangingResult>): void
```

向指定设备发起主动测距，获取目标设备的距离和信号强度等信息。典型应用场景包括：智能防丢与寻找、近场找物、数字钥匙等。

该接口的执行流程取决于本端设备与目标设备的星闪连接状态：

若本端设备已与目标设备建立了星闪连接，调用此接口会直接向目标设备发起测距。若本端设备与目标设备未建立星闪连接，该接口将执行以下流程：
1. 融合测距服务内部先尝试与目标设备建立连接，连接成功后进行配对和加密操作。配对时需要用户主动在设备上操作授权。如果用户拒绝授权或者超时未授权，本次测距将会停止，停止状态会通过
[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)接口注册的callback通知，停止后需在应用侧主动调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)接口停止测距并释放测距资源。
2. 连接完成后，测距服务会先查询目标设备是否支持对应的测距服务UUID，确认服务支持后自动发起测距；如果在连接后，
对端设备不支持测距服务UUID，融合测距服务内部会主动断开与对端设备已建立的连接，并通过回调通知测距停止。

开始测距后，可通过[onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md)实时监听测距状态变化，测距结果通过本接口中的入参callback返回。

成功启动测距后结果会频繁回调上报，建议根据实际需要在获取测距结果后及时调用stopRanging停止测距，业务需要时可再次发起测距，避免不必要的功耗损失。

使用测距接口前，需先通过[getRangingCapability](arkts-connectivity-ranging-getrangingcapability-f.md)确认设备支持对应的测距类型。

使用星闪HADM测距时，本端设备在发起主动测距后，无法使用被动测距模式。如需使用被动测距，需先调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)停止主动测距。

对同一设备连续重复调用[startRanging](arkts-connectivity-ranging-startranging-f.md)会提示设备已发起测距并返回错误码34900051。如需对同一设备再次发起测距，需先调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)停止之前的测距后重新调用。

如果启动测距时，对应类型的测距服务已下线，那么调用本接口时会抛出服务未使能错误码34900053。

接口入参需要按照要求填写，如果不符合要求接口会返回对应的错误码，详细要求见参数的定义。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [RangingParams](arkts-connectivity-ranging-rangingparams-i.md) | 是 | 目标设备的测距参数，包含设备的地址和测距能力类型。如果填入的参数不符合要求，接口会按照参数要求返回对应的错误码。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingResult](arkts-connectivity-ranging-rangingresult-i.md)&gt; | 是 | 测距结果回调，每次测距结果产生时触发回调。同时作为测距目标标识，需在调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)时传入相同引用以关联已启动的测距，因此在应用侧不要使用临时callback作为入参。同一callback可关联多个设备的测距会话，但如果调用[stopRanging](arkts-connectivity-ranging-stopranging-f.md)接口停止测距时未指定[params](arkts-connectivity-ranging-rangingparams-i.md)，接口将根据callback停止全部关联的测距设备，不建议多个设备共用同一测距回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900051](../errorcode-fusionConnectivity.md#34900051-该设备已发起测距) | The device has already initiated ranging. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-不支持指定类型的测距服务) | The specified type of ranging service is not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-测距服务关闭) | The ranging service is disabled. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-参数不符合业务规格) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
