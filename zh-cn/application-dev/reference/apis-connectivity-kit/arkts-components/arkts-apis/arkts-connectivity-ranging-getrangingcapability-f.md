# getRangingCapability

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## getRangingCapability

```TypeScript
function getRangingCapability(): Promise<RangingCapabilitySupported>
```

查询本端设备支持的测距能力，使用Promise异步回调。

建议先使用[isRangingSupported](arkts-connectivity-ranging-israngingsupported-f.md)判断本端是否支持测距特性。仅在特性支持的情况下才能使用融合测距的功能。获取成功后，使用Promise异步返回测距类型是否支持。仅当[nearlinkHadm](arkts-connectivity-ranging-rangingcapabilitysupported-i.md)值为true，才可以使用[startRanging](arkts-connectivity-ranging-startranging-f.md)发起星闪HADM测距，或使用[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)启动被动测距。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RangingCapabilitySupported](arkts-connectivity-ranging-rangingcapabilitysupported-i.md)&gt; | Promise对象，返回本端设备支持的测距类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-测距服务关闭) | The ranging service is disabled. |
