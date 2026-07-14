# @ohos.power (系统电源管理)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块主要提供设备电源状态管理相关系统接口，包括关机、重启设备、唤醒设备、使设备睡眠或休眠、设置电源模式、设置灭屏超时时间、刷新设备活动状态、配置电源键过滤策略、订阅/取消关机重启回调以及电源配置查询与设置等功能。适用于系统应用需要对设备电源状态进行管控的场景，如设备管理应用控制设备的开关机与休眠唤醒、省电模式切换、屏幕超时管理等，帮助开发者实现对设备电源行为的精细化管理与自动化控制。

> **说明：**
>
> 本模块首批接口从 API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.power (系统电源管理)](js-apis-power.md)。

## 导入模块

```js
import { power, BusinessError } from '@kit.BasicServicesKit';
```

## power.shutdown

shutdown(reason: string): void

系统关机。与reboot方法的区别：shutdown使设备完全关机不再运行，reboot使设备关机后自动重启。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| reason | string | 是    | 关机原因。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |


**示例：**

```js
try {
    power.shutdown('shutdown_test');
} catch (err) {
    console.error(`Failed to shutdown. Code: ${err.code}, message: ${err.message}`);
}
```

## power.reboot<sup>9+</sup>

reboot(reason: string): void

重启设备。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| reason | string | 是   | 重启原因。例如，"updater"表示重启后进入更新模式。传入空字符串时，系统将在重启后进入正常模式。|

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.reboot('reboot_test');
} catch (err) {
    console.error(`Failed to reboot. Code: ${err.code}, message: ${err.message}`);
}
```

## power.wakeup<sup>9+</sup>

wakeup(detail: string): void

唤醒设备，将设备从睡眠状态恢复到活动状态。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_MANAGER

API version 9-18，使用该接口无需权限；从 API version 19开始，需要申请“ohos.permission.POWER_MANAGER”权限。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| detail | string | 是   | 唤醒原因。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.wakeup('wakeup_test');
} catch (err) {
    console.error(`Failed to wakeup device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.suspend<sup>9+</sup>

suspend(isImmediate?: boolean): void

使设备进入睡眠状态。

调用此方法后设备将进入睡眠，如需恢复到活动状态，需调用[power.wakeup](#powerwakeup9)唤醒设备。

与hibernate方法的区别：suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠），hibernate为更深的休眠状态（休眠前可选择清理内存）。需快速恢复设备活动时选择suspend，需最大程度节省电量时选择hibernate。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_MANAGER

API version 9-18，使用该接口无需权限；从 API version 19开始，需要申请“ohos.permission.POWER_MANAGER”权限。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| isImmediate<sup>10+</sup> | boolean |  否  | 是否直接使设备进入睡眠状态。true表示灭屏后立即进入睡眠，不填该参数则默认为false，表示灭屏后由系统自动检测何时进入睡眠。如果只想做灭屏操作，建议不填参数。<br>**说明：** 从 API version 10开始，支持该参数。|


**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |

**示例：**

```js
try {
    power.suspend();
} catch (err) {
    console.error(`Failed to suspend device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode, callback: AsyncCallback&lt;void&gt;): void

设置当前设备的电源模式，不同的电源模式会影响设备的性能与功耗策略。使用callback异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_OPTIMIZATION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名   | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| mode     | [DevicePowerMode](js-apis-power.md#devicepowermode9) | 是   | 电源模式。各模式含义请参见[DevicePowerMode](js-apis-power.md#devicepowermode9)枚举说明。 |
| callback | AsyncCallback&lt;void&gt;            | 是   | 回调函数。当设置电源模式成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900301 | Setting the power mode failed. |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: BusinessError) => {
    if (err) {
        console.error(`Failed to set power mode. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('set power mode to MODE_PERFORMANCE');
});
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode): Promise&lt;void&gt;

设置当前设备的电源模式，不同的电源模式会影响设备的性能与功耗策略。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_OPTIMIZATION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型                                 | 必填 | 说明       |
| ------ | ------------------------------------ | ---- | ---------- |
| mode   | [DevicePowerMode](js-apis-power.md#devicepowermode9) | 是   | 电源模式。各模式含义请参见[DevicePowerMode](js-apis-power.md#devicepowermode9)枚举说明。 |

**返回值：**

| 类型                | 说明                                   |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900301 | Setting the power mode failed. |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err: BusinessError) => {
    console.error(`Failed to set power mode. Code: ${err.code}, message: ${err.message}`);
});
```

## power.setScreenOffTime<sup>12+</sup>

setScreenOffTime(timeout: number): void

设置灭屏超时时间。例如，在自助终端或展示设备场景下可设置较长的超时时间以保持屏幕常亮，在低电量场景下可设置较短的超时时间以节省电量。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_MANAGER

API version 12-18，使用该接口无需权限；从 API version 19开始，需要申请“ohos.permission.POWER_MANAGER”权限。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| timeout | number | 是    | 灭屏超时时间，单位是毫秒。大于0代表灭屏超时时间，-1代表恢复默认超时时间，传入其它值时抛出异常，错误码401。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.setScreenOffTime(30000);
} catch (err) {
    console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}
```

## power.hibernate<sup>12+</sup>

hibernate(clearMemory: boolean): void

休眠设备。

与suspend方法的区别：hibernate为更深的休眠状态（休眠前可选择清理内存），suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠）。需最大程度节省电量时选择hibernate，需快速恢复设备活动时选择suspend。适用于设备长时间闲置需要深度节能的场景。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_MANAGER

API version 12-18，使用该接口无需权限；从 API version 19开始，需要申请“ohos.permission.POWER_MANAGER”权限。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| clearMemory | boolean | 是    | 是否在进入休眠之前清理内存。true表示清理内存，false表示不清理内存。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |

**示例：**

```js
try {
    power.hibernate(true);
} catch (err) {
    console.error(`Failed to hibernate device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.refreshActivity<sup>20+</sup>

refreshActivity(reason: string): void

刷新设备活动状态（如：重设屏幕超时灭屏时间等）。

此接口仅在设备活动状态下生效。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REFRESH_USER_ACTION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| reason | string | 是    | 刷新设备活动状态的原因。仅在设备活动状态下生效，设备活动状态见[power.isActive](js-apis-power.md#powerisactive9)。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 4900201 |The device activity is being refreshed too frequently; the minimum time interval is 100 ms. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.refreshActivity('refreshActivity_test');
} catch (err) {
    console.error(`Failed to refresh activity. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerKeyFilteringStrategy<sup>21+</sup>

setPowerKeyFilteringStrategy(strategy: PowerKeyFilteringStrategy): void

设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。

电源键过滤策略见[power.PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21)接口。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| strategy | [PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21) | 是    | 电源键过滤策略，用于配置电源键事件的处理方式。各策略含义请参见[PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21)。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.setPowerKeyFilteringStrategy(power.PowerKeyFilteringStrategy.LONG_PRESS_FILTERING_ONCE);
} catch (err) {
    console.error(`Failed to set power key filtering strategy. Code: ${err.code}, message: ${err.message}`);
}
```

## power.registerShutdownCallback<sup>23+</sup>

registerShutdownCallback(callback: Callback&lt;boolean&gt;): void

订阅电源关机或重启的回调提醒。使用callback异步回调。调用此方法订阅回调后，可在不再需要时调用[power.unregisterShutdownCallback](#powerunregistershutdowncallback23)取消订阅，释放系统资源。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名   | 类型                         | 必填 | 说明                           |
| -------- | ---------------------------- | ---- | ------------------------------ |
| callback | Callback&lt;boolean&gt; | 是   | 回调函数，返回true表示重启；返回false表示关机。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.registerShutdownCallback((isReboot: boolean) => {
        console.info('device is reboot: ' + isReboot);
    });
    console.info('register shutdown callback success.');
} catch (err) {
    console.error(`Failed to register shutdown callback. Code: ${err.code}, message: ${err.message}`);
}
```

## power.unregisterShutdownCallback<sup>23+</sup>

unregisterShutdownCallback(callback?: Callback\<void>): void

取消订阅电源关机或重启的回调提醒。使用callback同步回调。此方法与[power.registerShutdownCallback](#powerregistershutdowncallback23)配对使用，必须在先调用registerShutdownCallback订阅回调后，再调用此方法取消订阅。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                           |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| callback | Callback&lt;void&gt; | 否   | 回调函数，无返回值。取消订阅成功后会调用该回调函数。不传入此参数时，取消订阅仍生效，但不会触发回调通知。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    power.unregisterShutdownCallback(() => {
        console.info('unsubscribe shutdown success.');
    });
    console.info('unregister shutdown callback success.');
} catch (err) {
    console.error(`Failed to unregister shutdown callback. Code: ${err.code}, message: ${err.message}`);
}
```

## power.getPowerConfig

getPowerConfig(sceneName: string): string

按场景名称查询电源配置值。例如，在系统电源管理应用中需要读取特定场景的电源配置参数时使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_CONFIG

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| sceneName | string | 是    | 电源配置的场景名称。最大长度128字节，不支持空字符串。超出长度限制或传入空字符串时返回错误码4900400。 |

**返回值：**

| 类型     | 说明         |
| ------ | ------------ |
| string | 返回指定场景名称对应的电源配置值，配置值的具体内容取决于所查询的场景名称。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4900400 | Invalid parameter. Possible causes: <br>1. The sceneName parameter is an empty string; <br>2. The length of sceneName parameter exceeds 128 bytes. |
| 4900501 | Failed to read the power configuration value. |

**示例：**

```js
try {
    let configVal = power.getPowerConfig('scene_name_test');
    console.info('get power config success, configVal: ' + configVal);
} catch (err) {
    console.error(`Failed to get power config. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerConfig

setPowerConfig(sceneName: string, value: string): void

根据场景名称设置电源配置值。例如，在系统电源管理应用中需要动态调整特定场景的电源配置参数时使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.POWER_CONFIG

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明    |
| ------ | ------ | ---- | ----- |
| sceneName | string | 是    | 电源配置的场景名称。最大长度128字节，不支持空字符串。超出长度限制或传入空字符串时返回错误码4900400。 |
| value | string | 是    | 电源配置值。最大长度128字节，不支持空字符串。超出长度限制或传入空字符串时返回错误码4900400。 |

**错误码：**

以下错误码的详细介绍请参见[系统电源管理错误码](errorcode-power.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4900400 | Invalid parameter. Possible causes: <br>1. The sceneName or value parameter is an empty string; <br>2. The length of sceneName parameter exceeds 128 bytes; <br>3. The length of value parameter exceeds 128 bytes. |
| 4900601 | Failed to write the power configuration value. |

**示例：**

```js
try {
    power.setPowerConfig('scene_name_test', 'value_test');
    console.info('set power config success');
} catch (err) {
    console.error(`Failed to set power config. Code: ${err.code}, message: ${err.message}`);
}
```