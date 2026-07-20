# @ohos.power (系统电源管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块主要提供查询屏幕状态、查询电源模式、检测待机模式等接口，还提供电源键过滤策略的配置能力。开发者可以使用该模块的接口获取设备的活动状态、电源模式、亮灭屏状态、待机低功耗状态等，适用于需要根据设备电源状态进行业务逻辑调整的场景，例如在低功耗模式下限制后台活动、在待机模式下优化续航策略等。

> **说明：**
>
> 本模块首批接口从 API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { power } from '@kit.BasicServicesKit';
```

## power.isActive<sup>9+</sup>

isActive(): boolean

检测当前设备是否处于活动状态。可用于应用根据设备活动状态调整行为，例如在设备非活动状态下暂停后台任务等。
- 有屏的设备亮屏时为活动状态，灭屏时为非活动状态。
- 无屏的设备非休眠时为活动状态，休眠时为非活动状态。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型                | 说明                                   |
| ------------------- | -------------------------------------- |
| boolean | 活动状态返回true，非活动状态返回false。 |

**示例：**

```js
let isActive = power.isActive();
console.info('power is active: ' + isActive);
```

## power.rebootDevice<sup>(deprecated)</sup>

rebootDevice(reason: string): void

重启设备。

> **说明：**
>
> 从 API version 7开始支持，从 API version 9开始废弃<!--Del-->。建议使用[power.reboot](js-apis-power-sys.md#powerreboot9)替代<!--DelEnd-->，替代接口能力仅对系统应用开放。

**需要权限：** ohos.permission.REBOOT，该权限仅系统应用可申请。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core


**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| reason | string | 是 | 重启原因。例如，"updater"表示重启后进入更新模式。不指定具体原因时，系统将在重启后进入正常模式。 |

**示例：**

```js
power.rebootDevice('reboot_test');
```

## power.getPowerMode<sup>9+</sup>

getPowerMode(): DevicePowerMode

获取当前设备的电源模式。不同电源模式对应不同的设备行为策略，开发者可根据返回的模式值调整应用行为以适配当前模式。各模式定义及说明请参见[DevicePowerMode](#devicepowermode9)。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型                                 | 说明       |
| ------------------------------------ | ---------- |
| [DevicePowerMode](#devicepowermode9) | 当前设备的电源模式，取值包括标准模式、省电模式、性能模式、超级省电模式等。 |

**示例：**

```js
let mode = power.getPowerMode();
console.info('power mode: ' + mode);
```

## power.isStandby<sup>10+</sup>

isStandby(): boolean

检测当前设备是否进入待机低功耗续航模式。待机模式下系统会采取降低功耗的策略，开发者应据此调整应用的后台任务和资源使用策略，避免在待机时执行高耗能操作。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型                | 说明                                   |
| ------------------- | -------------------------------------- |
| boolean | 进入待机模式返回true，未进入待机模式返回false。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |

**示例：**

```js
try {
    let isStandby = power.isStandby();
    console.info('device is in standby: ' + isStandby);
} catch (err) {
    console.error(`Failed to check isStandby. Code: ${err.code}, message: ${err.message}`);
}
```

## power.isScreenOn<sup>(deprecated)</sup>

isScreenOn(callback: AsyncCallback&lt;boolean&gt;): void

检测当前设备的亮灭屏状态。使用callback异步回调。

> **说明：**
>
> 从 API version 7开始支持，从 API version 9开始废弃，建议使用[power.isActive](#powerisactive9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名   | 类型                         | 必填 | 说明                                                         |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。当检测成功，err为undefined，data为获取到的亮灭屏状态，返回true表示亮屏，返回false表示灭屏；否则err为错误对象。 |

**示例：**

```js
power.isScreenOn((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('screen on status is ' + data);
});
```

## power.isScreenOn<sup>(deprecated)</sup>

isScreenOn(): Promise&lt;boolean&gt;

检测当前设备的亮灭屏状态。使用Promise异步回调。

> **说明：**
>
> 从 API version 7开始支持，从 API version 9开始废弃，建议使用[power.isActive](#powerisactive9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**
| 类型                   | 说明                                               |
| ---------------------- | -------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示亮屏；返回false表示灭屏。 |

**示例：**

```js
power.isScreenOn()
.then((data: boolean) => {
    console.info('screen on status is ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
});
```

## DevicePowerMode<sup>9+</sup>

表示电源模式的枚举值。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

| 名称                    | 值   | 说明                   |
| ----------------------- | ---- | ---------------------- |
| MODE_NORMAL             | 600  | 表示标准模式，默认值。 |
| MODE_POWER_SAVE         | 601  | 表示省电模式。         |
| MODE_PERFORMANCE        | 602  | 表示性能模式。         |
| MODE_EXTREME_POWER_SAVE | 603  | 表示超级省电模式。     |
| MODE_CUSTOM_POWER_SAVE<sup>20+</sup>  | 650  | 表示自定义省电模式。     |

## PowerKeyFilteringStrategy<sup>21+</sup>

表示电源键过滤策略。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

| 名称                    | 值   | 说明                   |
| ----------------------- | ---- | ---------------------- |
| DISABLE_LONG_PRESS_FILTERING | 0  | 表示禁用电源键长按事件的过滤策略，默认值。 |
| LONG_PRESS_FILTERING_ONCE | 1  | 表示仅过滤当前电源键长按事件，下一次不过滤。 |