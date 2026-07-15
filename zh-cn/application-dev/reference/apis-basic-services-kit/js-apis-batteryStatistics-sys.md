# @ohos.batteryStatistics (耗电统计)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块提供软硬件耗电统计信息的查询接口，支持查询应用和硬件单元的耗电量与耗电百分比，适用于开发者需要监控和分析设备耗电情况的场景，便于定位高耗电应用或硬件组件，从而优化应用的能耗表现。

> **说明：**
>
> - 本模块首批接口从 API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。

## 导入模块

```js
import { batteryStats, BusinessError } from '@kit.BasicServicesKit';
```

## batteryStats.getBatteryStats

getBatteryStats(): Promise<Array&lt;BatteryStatsInfo&gt;>

获取耗电信息列表，用于电池监控应用查看各应用及硬件的耗电情况。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**返回值：**

| 类型                                                  | 说明                            |
| ----------------------------------------------------- | ------------------------------- |
| Promise<Array<[BatteryStatsInfo](#batterystatsinfo)>> | Promise对象，返回耗电信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
batteryStats.getBatteryStats()
.then((data: batteryStats.BatteryStatsInfo[]) => {
    console.info('battery statistics info: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
});
```

## batteryStats.getBatteryStats

getBatteryStats(callback: AsyncCallback<Array&lt;BatteryStatsInfo&gt;>): void

获取耗电信息列表，用于电池监控应用查看各应用及硬件的耗电情况。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<Array<[BatteryStatsInfo](#batterystatsinfo)>> | 是   | 回调函数。当获取耗电信息列表成功，err为undefined，data为获取到的Array<[BatteryStatsInfo](#batterystatsinfo)>；否则为错误对象；AsyncCallback封装了一个BatteryStatsInfo类型的接口。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
batteryStats.getBatteryStats((err: BusinessError, data: batteryStats.BatteryStatsInfo[]) => {
    if (err) {
        console.error(`Failed to get battery statistics. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('battery statistics info: ' + data);
    }
});
```

## batteryStats.getAppPowerValue

getAppPowerValue(uid: number): number

获取应用的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同应用耗电占比，请使用getAppPowerPercent获取相对百分比。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**参数：**

| 参数名 | 类型   | 必填 | 说明        |
| ------ | ------ | ---- | ----------- |
| uid    | number | 是   | 应用的UID，用于指定查询耗电量的目标应用。可通过[bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)等接口获取应用UID。 |

**返回值：**

| 类型   | 说明                              |
| ------ | --------------------------------- |
| number | UID对应应用的耗电量，单位毫安时。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```js
try {
    let value = batteryStats.getAppPowerValue(10021); // 10021为示例UID，实际使用时需通过bundleManager.getUidByBundleName等接口获取应用UID
    console.info('battery statistics value of app is: ' + value);
} catch (err) {
    console.error(`Failed to get battery statistics value of app. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getAppPowerPercent

getAppPowerPercent(uid: number): number

获取应用的耗电百分比，该百分比表示应用耗电量占总耗电量的比例。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**参数：**

| 参数名 | 类型   | 必填 | 说明        |
| ------ | ------ | ---- | ----------- |
| uid    | number | 是   | 应用的UID，用于指定查询耗电百分比的目标应用。可通过[bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)等接口获取应用UID。 |

**返回值：**

| 类型   | 说明                      |
| ------ | ------------------------- |
| number | UID对应应用的耗电百分比，取值范围是[0.00，1.00]。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```js
try {
    let percent = batteryStats.getAppPowerPercent(10021); // 10021为示例UID，实际使用时需通过bundleManager.getBundleInfoForSelf等接口获取应用UID
    console.info('battery statistics percent of app is: ' + percent);
} catch (err) {
    console.error(`Failed to get battery statistics percent of app. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getHardwareUnitPowerValue

getHardwareUnitPowerValue(type: ConsumptionType): number

根据耗电类型获取硬件单元的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同硬件单元耗电占比，请使用getHardwareUnitPowerPercent获取相对百分比。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**参数：**

| 参数名 | 类型                                | 必填 | 说明           |
| ------ | ----------------------------------- | ---- | -------------- |
| type   | [ConsumptionType](#consumptiontype) | 是   | 电量消耗类型，用于指定要查询的硬件单元耗电类型。可选值参见[ConsumptionType](#consumptiontype)，如CONSUMPTION_TYPE_SCREEN用于查询屏幕耗电、CONSUMPTION_TYPE_BLUETOOTH用于查询蓝牙耗电、CONSUMPTION_TYPE_WIFI用于查询无线网耗电等。 |

**返回值：**

| 类型   | 说明                                       |
| ------ | ------------------------------------------ |
| number | 电量消耗类型对应硬件的耗电量，单位毫安时。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    let powerValue = batteryStats.getHardwareUnitPowerValue(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics value of hardware is: ' + powerValue);
} catch (err) {
    console.error(`Failed to get battery statistics value of hardware. Code: ${err.code}, message: ${err.message}`);
}
```

## batteryStats.getHardwareUnitPowerPercent

getHardwareUnitPowerPercent(type: ConsumptionType): number

根据耗电类型获取硬件单元的耗电百分比，该百分比表示指定硬件单元耗电量占总耗电量的比例。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**参数：**

| 参数名 | 类型                                | 必填 | 说明           |
| ------ | ----------------------------------- | ---- | -------------- |
| type   | [ConsumptionType](#consumptiontype) | 是   | 电量消耗类型，用于指定要查询的硬件单元耗电百分比类型。可选值参见[ConsumptionType](#consumptiontype)，如CONSUMPTION_TYPE_SCREEN用于查询屏幕耗电百分比、CONSUMPTION_TYPE_BLUETOOTH用于查询蓝牙耗电百分比、CONSUMPTION_TYPE_WIFI用于查询无线网耗电百分比等。 |

**返回值：**

| 类型   | 说明                               |
| ------ | ---------------------------------- |
| number | 电量消耗类型对应硬件的耗电百分比，取值范围是[0.00，1.00]。 |

**错误码：**

以下错误码的详细介绍请参见[耗电统计错误码](errorcode-batteryStatistics.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4600101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**示例：**

```js
try {
    let percent = batteryStats.getHardwareUnitPowerPercent(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics percent of hardware is: ' + percent);
} catch (err) {
    console.error(`Failed to get battery statistics percent of hardware. Code: ${err.code}, message: ${err.message}`);
}
```

## BatteryStatsInfo

设备软硬件的耗电信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

### 属性

| 名称  | 类型                                | 只读 | 可选 | 说明                   |
| ----- | ----------------------------------- | ---- | ---- | ---------------------- |
| uid   | number                              | 否   | 否   | 耗电信息对应的应用UID。  |
| type  | [ConsumptionType](#consumptiontype) | 否   | 否   | 耗电信息的消耗类型。   |
| power | number                              | 否   | 否   | 耗电的值，单位毫安时。 |

## ConsumptionType

表示电量消耗类型的枚举值。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

| 名称                       | 值   | 说明                          |
| -------------------------- | ---- | ----------------------------- |
| CONSUMPTION_TYPE_INVALID   | -17  | 表示电量消耗类型未知。        |
| CONSUMPTION_TYPE_APP       | -16  | 表示应用消耗的电量类型。      |
| CONSUMPTION_TYPE_BLUETOOTH | -15  | 表示蓝牙消耗的电量类型。      |
| CONSUMPTION_TYPE_IDLE      | -14  | 表示CPU空闲时消耗的电量类型。 |
<<<<<<< HEAD
| CONSUMPTION_TYPE_PHONE     | -13  | 表示通话消耗的电量类型。  |
| CONSUMPTION_TYPE_RADIO     | -12  | 表示蜂窝通讯消耗的电量类型。  |
=======
| CONSUMPTION_TYPE_PHONE     | -13  | 表示通话来电消耗的电量类型。  |
| CONSUMPTION_TYPE_RADIO     | -12  | 表示无线通信消耗的电量类型。  |
| CONSUMPTION_TYPE_SCREEN    | -11  | 表示屏幕消耗的电量类型。      |
| CONSUMPTION_TYPE_USER      | -10  | 表示用户消耗的电量类型。      |
| CONSUMPTION_TYPE_WIFI      | -9   | 表示无线网消耗的电量类型。    |
