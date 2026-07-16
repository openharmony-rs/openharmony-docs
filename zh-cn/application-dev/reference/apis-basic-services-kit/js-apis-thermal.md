# @ohos.thermal (热管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块提供热管理相关的接口，包括热档位查询及注册回调等功能。系统根据设备温度阈值将热状态划分为多个档位层级（参见[ThermalLevel](#thermallevel)），当设备温度跨越档位阈值时触发回调通知，开发者可根据档位等级执行相应的业务降级策略。

> **说明：**
>
> 本模块首批接口从 API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import {thermal} from '@kit.BasicServicesKit';
```

## thermal.registerThermalLevelCallback<sup>9+</sup>

registerThermalLevelCallback(callback: Callback&lt;ThermalLevel&gt;): void

订阅热档位变化时的回调提醒。当设备温度跨越档位阈值导致热档位发生变化时，系统自动触发回调通知，通过callback返回变化后的热档位等级。使用callback异步回调。

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名   | 类型                         | 必填 | 说明                           |
| -------- | ---------------------------- | ---- | ------------------------------ |
| callback | Callback&lt;[ThermalLevel](#thermallevel)&gt; | 是   | 回调函数，返回变化后的热档位。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```js
try {
    thermal.registerThermalLevelCallback((level: thermal.ThermalLevel) => {
        console.info('thermal level is: ' + level);
    });
    console.info('register thermal level callback success.');
} catch (err) {
    console.error(`Failed to register thermal level callback. Code: ${err.code}, message: ${err.message}`);
}
```

## thermal.unregisterThermalLevelCallback<sup>9+</sup>

unregisterThermalLevelCallback(callback?: Callback\<void>): void

取消订阅热档位变化时的回调提醒。使用callback异步回调。此方法与[thermal.registerThermalLevelCallback](#thermalregisterthermallevelcallback9)配对使用，用于取消先前注册的热档位回调。

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                           |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| callback | Callback&lt;void&gt; | 否   | 回调函数，用来执行取消热档位变化回调后的资源回收等操作，无返回值。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

```js
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch (err) {
    console.error(`Failed to unregister thermal level callback. Code: ${err.code}, message: ${err.message}`);
}
```

## thermal.getLevel<sup>9+</sup>

getLevel(): ThermalLevel

获取当前热档位信息。系统根据设备温度实时判定当前所处的热档位层级并返回对应等级，开发者可据此执行相应的业务降级策略。

**系统能力：** SystemCapability.PowerManager.ThermalManager


**返回值：**

| 类型         | 说明         |
| ------------ | ------------ |
| [ThermalLevel](#thermallevel) | 当前设备的热档位等级，反映设备的温度状态，可用于指导业务的热控策略调整。 |

**示例：**

```js
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```

## thermal.subscribeThermalLevel<sup>(deprecated)</sup>

subscribeThermalLevel(callback: AsyncCallback&lt;ThermalLevel&gt;): void

订阅热档位变化时的回调提醒。使用callback异步回调。此方法需与[thermal.unsubscribeThermalLevel](#thermalunsubscribethermalleveldeprecated)配对使用，在不再需要监听时取消订阅。

> **说明：**
>
> 从 API version 8开始支持，从 API version 9开始废弃。建议使用[thermal.registerThermalLevelCallback](#thermalregisterthermallevelcallback9)替代。

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名   | 类型                              | 必填 | 说明                                                         |
| -------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;[ThermalLevel](#thermallevel)&gt; | 是   | 回调函数，返回变化后的热档位。|

**示例：**

```js
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    if (err) {
        console.error('subscribe thermal level failed, err: ' + err);
        return;
    }
    console.info('thermal level is: ' + level);
});
```

## thermal.unsubscribeThermalLevel<sup>(deprecated)</sup>

unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void

取消订阅热档位变化时的回调提醒。使用callback异步回调。此方法与[thermal.subscribeThermalLevel](#thermalsubscribethermalleveldeprecated)配对使用，用于取消先前订阅的热档位回调。

> **说明：**
>
> 从 API version 8开始支持，从 API version 9开始废弃。建议使用[thermal.unregisterThermalLevelCallback](#thermalunregisterthermallevelcallback9)替代。

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                           |
| -------- | ------------------------- | ---- | ---------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | 否   | 回调函数，用来执行取消热档位变化回调后的资源回收等操作，无返回值。 |

**示例：**

```js
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```

## thermal.getThermalLevel<sup>(deprecated)</sup>

getThermalLevel(): ThermalLevel

获取当前热档位信息。

> **说明：**
>
> 从 API version 8开始支持，从 API version 9开始废弃。建议使用[thermal.getLevel](#thermalgetlevel9)替代。

**系统能力：** SystemCapability.PowerManager.ThermalManager

**返回值：**

| 类型           | 说明     |
| ------------ | ------ |
| [ThermalLevel](#thermallevel) | 当前设备的热档位等级，反映设备的温度状态，可用于指导业务的热控策略调整。 |

**示例：**

```js
let level = thermal.getThermalLevel();
console.info('thermal level is: ' + level);
```

## ThermalLevel

热档位信息。

热档位从COOL到ESCAPE逐级递进，各级别对应的设备状态与业务动作建议如下表所示。

**系统能力：** SystemCapability.PowerManager.ThermalManager

| 名称       | 值   | 说明                                                         |
| ---------- | ---- | ------------------------------------------------------------ |
| COOL       | 0    | 表明设备处于清凉状态，业务执行不受热控的限制。             |
| NORMAL     | 1    | 表明设备温度正常，但邻近温热状态，无感知业务应降低规格和负载。 |
| WARM       | 2    | 表明设备进入温热状态，无感知业务应暂停或延迟运行。 |
| HOT        | 3    | 表明设备发热明显，无感知业务应停止，非关键业务应降低规格及负载。 |
| OVERHEATED | 4    | 表明设备发热严重，无感知业务与非关键业务应停止，前台关键业务应降低规格及负载。 |
| WARNING    | 5    | 表明设备过热即将进入紧急状态，整机资源供给大幅降低，停止所有非关键业务，前台关键业务应降低至最低规格。 |
| EMERGENCY  | 6    | 表明设备已经进入过热紧急状态，整机资源供给降至最低，设备功能受限，仅保留基础功能可用。 |
| ESCAPE<sup>11+</sup>     | 7    | 表明设备即将进入热逃生状态，所有业务将被强制停止，业务需做好逃生措施，例如保存重要数据等。 <br>**说明**: 从 API version 11开始支持。|
