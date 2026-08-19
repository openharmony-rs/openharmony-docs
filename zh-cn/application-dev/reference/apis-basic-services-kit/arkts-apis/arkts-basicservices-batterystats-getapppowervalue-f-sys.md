# getAppPowerValue（系统接口）

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getAppPowerValue

```TypeScript
function getAppPowerValue(uid: int): double
```

获取应用的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同应用耗电占比，请使用[getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md)获取相对百分比。

**起始版本：** 23

<!--Device-batteryStats-function getAppPowerValue(uid: int): double--><!--Device-batteryStats-function getAppPowerValue(uid: int): double-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | 应用的UID，用于指定查询耗电量的目标应用。 可通过[bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)等接口获取应用UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | UID对应应用的耗电量，单位毫安时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [4600101](../errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
try {
    let value = batteryStats.getAppPowerValue(10021);
    console.info('battery statistics value of app is: ' + value);
} catch(err) {
    console.error('get battery statistics value of app failed, err: ' + err);
}
```

