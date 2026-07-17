# getAppPowerValue（系统接口）

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getAppPowerValue

```TypeScript
function getAppPowerValue(uid: number): number
```

获取应用的耗电量，单位毫安时。

**起始版本：** 8

<!--Device-batteryStats-function getAppPowerValue(uid: int): double--><!--Device-batteryStats-function getAppPowerValue(uid: int): double-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 应用的UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | UID对应应用的耗电量，单位毫安时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    let value = batteryStats.getAppPowerValue(10021); // 10021为示例UID，实际使用时需通过bundleManager.getUidByBundleName等接口获取应用UID
    console.info('battery statistics value of app is: ' + value);
} catch (err) {
    console.error(`Failed to get battery statistics value of app. Code: ${err.code}, message: ${err.message}`);
}

```

