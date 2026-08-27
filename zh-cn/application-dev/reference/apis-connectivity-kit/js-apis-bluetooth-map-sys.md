# @ohos.bluetooth.map (蓝牙map模块)(系统接口)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

map模块提供了基于蓝牙消息访问配置（[MAP](../../connectivity/bluetooth/terminology.md#map)，Message Access Profile）协议访问远端设备消息（如短信、邮件等）相关功能的方法，支持断开MAP服务连接、设置和获取消息访问权限等能力，适用于需要通过蓝牙与远端设备进行消息数据交互的场景。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.bluetooth.map (蓝牙map模块)](js-apis-bluetooth-map.md)。


## 导入模块

```js
import { map } from '@kit.ConnectivityKit';
```


### disconnect

disconnect(deviceId: string): void

断开连接设备的map服务。适用于设备切换、连接异常恢复或用户主动断开蓝牙信息同步等场景。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

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
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### setMessageAccessAuthorization

setMessageAccessAuthorization(deviceId: string, authorization: AccessAuthorization): Promise&lt;void&gt;

设置信息的访问权限。使用Promise异步回调。适用于蓝牙消息同步前进行权限授予或撤销的场景，如用户在车载、可穿戴设备上管理蓝牙消息读取权限。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型     | 必填   | 说明                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | 是    | 表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| authorization | [AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11) | 是    | 表示对信息访问的授权状态，例如允许访问（ACCESS_ALLOWED）、拒绝访问（ACCESS_DENIED）等。具体枚举值及含义详见[AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11)。 |

**返回值：**

| 类型                                              | 说明                |
| ------------------------------------------------- | ------------------- |
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
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.setMessageAccessAuthorization('XX:XX:XX:XX:XX:XX', 0).then(() => {
        console.info('setMessageAccessAuthorization');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getMessageAccessAuthorization

getMessageAccessAuthorization(deviceId: string): Promise&lt;AccessAuthorization&gt;

获取信息的访问权限。使用Promise异步回调。适用于在蓝牙消息同步前查询当前设备是否已获得信息读取授权的场景。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型     | 必填   | 说明                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | 是    | 表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型                                              | 说明                |
| ------------------------------------------------- | ------------------- |
| Promise&lt;[AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11)&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

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
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.getMessageAccessAuthorization('XX:XX:XX:XX:XX:XX').then((authorization) => {
        console.info('authorization ' + authorization);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```