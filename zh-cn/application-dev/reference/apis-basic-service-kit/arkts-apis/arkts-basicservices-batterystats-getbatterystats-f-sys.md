# getBatteryStats（系统接口）

## getBatteryStats

```TypeScript
function getBatteryStats(): Promise<Array<BatteryStatsInfo>>
```

获取耗电信息列表。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-batteryStats-function getBatteryStats(): Promise<Array<BatteryStatsInfo>>--><!--Device-batteryStats-function getBatteryStats(): Promise<Array<BatteryStatsInfo>>-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)&gt;&gt; | Promise对象，返回耗电信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
batteryStats.getBatteryStats()
.then((data: batteryStats.BatteryStatsInfo[]) => {
    console.info('battery statistics info: ' + data);
})
.catch((err: Error) => {
    console.error('get battery statistics failed, err: ' + err);
});
```


## getBatteryStats

```TypeScript
function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void
```

获取耗电信息列表。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-batteryStats-function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void--><!--Device-batteryStats-function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)&gt;&gt; | 是 | 回调函数。当获取耗电信息列表成功，err为undefined，data为获取到的Array&lt; [BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md#BatteryStatsInfo（系统接口）)&gt;>；否则为错误对象；AsyncCallback封装了一个BatteryStatsInfo类型的接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
batteryStats.getBatteryStats((err: Error, data : batteryStats.BatteryStatsInfo[]) => {
    if (typeof err === 'undefined') {
        console.info('battery statistics info: ' + data);
    } else {
        console.error('get battery statistics failed, err: ' + err);
    }
});
```

ArkTS-Sta示例：

```TypeScript
batteryStats.getBatteryStats((err: Error | null, data : batteryStats.BatteryStatsInfo[] | undefined) => {
    if (!err) {
        console.info('battery statistics info: ' + data);
    } else {
        console.error('get battery statistics failed, err: ' + err);
    }
});
```

