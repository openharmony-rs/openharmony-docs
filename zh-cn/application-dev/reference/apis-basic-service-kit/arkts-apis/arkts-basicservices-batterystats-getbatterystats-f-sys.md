# getBatteryStats（系统接口）

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

<a id="getbatterystats"></a>
## getBatteryStats

```TypeScript
function getBatteryStats(): Promise<Array<BatteryStatsInfo>>
```

获取耗电信息列表。使用Promise异步回调。

**起始版本：** 8

<!--Device-batteryStats-function getBatteryStats(): Promise<Array<BatteryStatsInfo>>--><!--Device-batteryStats-function getBatteryStats(): Promise<Array<BatteryStatsInfo>>-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BatteryStatsInfo&gt;&gt; | Promise对象，返回耗电信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
batteryStats.getBatteryStats()
.then((data: batteryStats.BatteryStatsInfo[]) => {
    console.info('battery statistics info: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
});

```


<a id="getbatterystats-1"></a>
## getBatteryStats

```TypeScript
function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void
```

获取耗电信息列表。使用callback异步回调。

**起始版本：** 8

<!--Device-batteryStats-function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void--><!--Device-batteryStats-function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;BatteryStatsInfo&gt;&gt; | 是 | 回调函数。当获取耗电信息列表成功，err为undefined，data为获取到的Array<[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)>>；否则为错误对象；AsyncCallback封装了一个BatteryStatsInfo类型的接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
batteryStats.getBatteryStats((err: BusinessError, data: batteryStats.BatteryStatsInfo[]) => {
    if (err) {
        console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('battery statistics info: ' + data);
    }
});

```

