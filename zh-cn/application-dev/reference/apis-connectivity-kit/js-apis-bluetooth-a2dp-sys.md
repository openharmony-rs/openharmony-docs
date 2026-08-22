# @ohos.bluetooth.a2dp (蓝牙a2dp模块)(系统接口)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

a2dp模块提供了访问蓝牙音频接口的方法，支持A2DP服务连接管理、绝对音量能力查询与开关控制、编码器信息获取与设置、自动播放控制等功能，适用于系统应用对蓝牙音频设备进行连接与能力管理的场景。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.bluetooth.a2dp (蓝牙a2dp模块)](js-apis-bluetooth-a2dp.md)。


## 导入模块

```js
import { a2dp } from '@kit.ConnectivityKit';
```


### connect

connect(deviceId: string): void

发起设备的a2dp服务连接请求。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.               |
|2900003 | Bluetooth disabled.       |
|2900004 | Profile not supported.      |
|2900099 | Operation failed.              |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### disconnect

disconnect(deviceId: string): void

断开设备的a2dp服务连接。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### isAbsoluteVolumeSupported<sup>11+</sup>

isAbsoluteVolumeSupported(deviceId: string, callback: AsyncCallback&lt;boolean&gt;): void

获取设备是否支持绝对音量能力。该接口的返回值影响[isAbsoluteVolumeEnabled](#isabsolutevolumeenabled11)、[enableAbsoluteVolume](#enableabsolutevolume11)、[disableAbsoluteVolume](#disableabsolutevolume11)接口的使用。使用Callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当接口调用返回成功，err为undefined，data为获取到的设备是否支持绝对音量结果，true表示设备支持绝对音量能力，false表示设备不支持绝对音量能力；否则为错误对象。 |


**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.isAbsoluteVolumeSupported('XX:XX:XX:XX:XX:XX', (err, supported) => {
        if (err) {
            console.error('isAbsoluteVolumeSupported error');
            return;
        }
        console.info('device support absolute volume ' + supported);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### isAbsoluteVolumeSupported<sup>11+</sup>

isAbsoluteVolumeSupported(deviceId: string): Promise&lt;boolean&gt;

获取设备是否支持绝对音量能力。该接口的返回值影响[isAbsoluteVolumeEnabled](#isabsolutevolumeenabled11)、[enableAbsoluteVolume](#enableabsolutevolume11)、[disableAbsoluteVolume](#disableabsolutevolume11)接口的使用。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备支持绝对音量能力；返回false表示设备不支持绝对音量能力。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.isAbsoluteVolumeSupported('XX:XX:XX:XX:XX:XX').then((supported) => {
        console.info('device support absolute volume ' + supported);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### isAbsoluteVolumeEnabled<sup>11+</sup>

isAbsoluteVolumeEnabled(deviceId: string, callback: AsyncCallback&lt;boolean&gt;): void

获取设备绝对音量能力是否开启。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当接口调用返回成功，err为undefined，data为获取到的绝对音量能力开启结果，true表示设备绝对音量能力已开启，false表示设备绝对音量能力未开启；否则为错误对象。 |


**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.isAbsoluteVolumeEnabled('XX:XX:XX:XX:XX:XX', (err, enabled) => {
        if (err) {
            console.error('isAbsoluteVolumeEnabled error');
            return;
        }
        console.info('device absolute volume enable ' + enabled);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### isAbsoluteVolumeEnabled<sup>11+</sup>

isAbsoluteVolumeEnabled(deviceId: string): Promise&lt;boolean&gt;

获取设备绝对音量能力是否开启。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备绝对音量能力开启；返回false表示设备绝对音量能力未开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.isAbsoluteVolumeEnabled('XX:XX:XX:XX:XX:XX').then((enabled) => {
        console.info('device absolute volume enable ' + enabled);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### enableAbsoluteVolume<sup>11+</sup>

enableAbsoluteVolume(deviceId: string, callback: AsyncCallback&lt;void&gt;): void

开启设备绝对音量能力。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。如果成功，err为undefined，否则为错误对象。 |


**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.enableAbsoluteVolume('XX:XX:XX:XX:XX:XX', (err) => {
        if (err) {
            console.error(`Failed to enable absolute volume. Code: ${err.code}, message: ${err.message}`);
            return;
        }
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### enableAbsoluteVolume<sup>11+</sup>

enableAbsoluteVolume(deviceId: string): Promise&lt;void&gt;

开启设备绝对音量能力。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.enableAbsoluteVolume('XX:XX:XX:XX:XX:XX').then(() => {
        console.info('enableAbsoluteVolume');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### disableAbsoluteVolume<sup>11+</sup>

disableAbsoluteVolume(deviceId: string, callback: AsyncCallback&lt;void&gt;): void

关闭设备绝对音量能力。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。如果成功，err为undefined，否则为错误对象。 |


**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.disableAbsoluteVolume('XX:XX:XX:XX:XX:XX', (err) => {
        if (err) {
            console.error(`Failed to disable absolute volume. Code: ${err.code}, message: ${err.message}`);
            return;
        }
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### disableAbsoluteVolume<sup>11+</sup>

disableAbsoluteVolume(deviceId: string): Promise&lt;void&gt;

关闭设备绝对音量能力。需先确认设备支持绝对音量（参考[isAbsoluteVolumeSupported](#isabsolutevolumesupported11)）。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.disableAbsoluteVolume('XX:XX:XX:XX:XX:XX').then(() => {
        console.info('disableAbsoluteVolume');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getCurrentCodecInfo<sup>11+</sup>

getCurrentCodecInfo(deviceId: string): CodecInfo

获取当前编码器信息。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| [CodecInfo](js-apis-bluetooth-a2dp.md#codecinfo11)| 当前编码器信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let codecInfo : a2dp.CodecInfo = a2dpSrc.getCurrentCodecInfo('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getCurrentFullCodecInfo<sup>19+</sup>

getCurrentFullCodecInfo(deviceId: string): CodecInfoList[]

获取当前设备支持的全量编码器能力集合。与[getCurrentCodecInfo](#getcurrentcodecinfo11)相比，本接口返回设备支持的全量编码器能力集合，而getCurrentCodecInfo仅返回当前正在使用的编码器信息；如需获取设备完整编码能力请使用本接口，如仅需获取当前编码器信息请使用getCurrentCodecInfo。调用此接口前，需确保当前设备为活跃设备。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| [CodecInfoList](js-apis-bluetooth-a2dp.md#codecinfolist19)[]| 当前设备支持的编码器能力集合。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |
|2902008 | Current device is not an active device.  |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let codecInfoList : a2dp.CodecInfoList[] = a2dpSrc.getCurrentFullCodecInfo('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### setCurrentCodecInfo<sup>11+</sup>

setCurrentCodecInfo(deviceId: string, codecInfo: CodecInfo): void

设置当前编码器信息。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| codecInfo | [CodecInfo](js-apis-bluetooth-a2dp.md#codecinfo11) | 是    | 编码器信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |   

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let codecInfo : a2dp.CodecInfo = {
        codecType: 0,
        codecBitsPerSample: 1,
        codecChannelMode: 2,
        codecSampleRate: 1
    };
    a2dpSrc.setCurrentCodecInfo('XX:XX:XX:XX:XX:XX', codecInfo);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### disableAutoPlay<sup>12+</sup>

disableAutoPlay(deviceId: string, duration: number): Promise&lt;void&gt;

限制设备在连接成功的若干毫秒内播放音乐，常用于连接车载蓝牙或蓝牙音箱时避免音频突然自动播放打断用户。可通过[enableAutoPlay](#enableautoplay12)取消该限制，通过[getAutoPlayDisabledDuration](#getautoplaydisabledduration12)查询当前拦截时长。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |
| duration | number | 是    | 拦截时长，取值范围：[3000, 20000]，单位：ms。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let durationNumber = 5000;
    a2dpSrc.disableAutoPlay('XX:XX:XX:XX:XX:XX', durationNumber).then(() => {
        console.info('disableAutoPlay');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### enableAutoPlay<sup>12+</sup>

enableAutoPlay(deviceId: string): Promise&lt;void&gt;

允许设备在连接成功后自动播放音乐，适用于需要恢复自动播放行为的场景，如用户主动确认后允许蓝牙设备自动续播音乐。可通过[disableAutoPlay](#disableautoplay12)设置拦截时长限制自动播放，通过[getAutoPlayDisabledDuration](#getautoplaydisabledduration12)查询当前状态。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.enableAutoPlay('XX:XX:XX:XX:XX:XX').then(() => {
        console.info('enableAutoPlay');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### getAutoPlayDisabledDuration<sup>12+</sup>

getAutoPlayDisabledDuration(deviceId: string): Promise&lt;number&gt;

获取拦截时长或自动播放开关，用于查询当前设备是否被限制自动播放及限制时长，常配合disableAutoPlay和enableAutoPlay使用以管理自动播放状态。返回的拦截时长由[disableAutoPlay](#disableautoplay12)设置，自动播放状态由[enableAutoPlay](#enableautoplay12)控制。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，格式为XX:XX:XX:XX:XX:XX，其中X为十六进制字符（0-9、A-F），例如："00:1A:2B:3C:4D:5E"。 |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;number&gt; | 以Promise的形式返回结果。number为返回的拦截时长，单位：ms。如果返回-1，则表示允许设备在连接成功后自动播放音乐。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.getAutoPlayDisabledDuration('XX:XX:XX:XX:XX:XX').then((data: number) => {
        console.info('number' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```