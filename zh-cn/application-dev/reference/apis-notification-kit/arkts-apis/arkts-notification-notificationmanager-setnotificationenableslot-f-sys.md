# setNotificationEnableSlot（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setNotificationEnableSlot

```TypeScript
function setNotificationEnableSlot(
    bundle: BundleOption,
    type: SlotType,
    enable: boolean,
    callback: AsyncCallback<void>
  ): void
```

设置指定应用的指定渠道类型的使能状态。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | 是 | 应用的包信息。 |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 指定渠道类型。 |
| enable | boolean | 是 | 使能状态（true：使能，false：禁止）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设置渠道使能回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space.<br>**适用版本：** 11+ |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// setNotificationEnableSlot
let setNotificationEnableSlotCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`setNotificationEnableSlot failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info('setNotificationEnableSlot success');
    }
};
notificationManager.setNotificationEnableSlot(
    { bundle: 'ohos.samples.notification', },
    notificationManager.SlotType.SOCIAL_COMMUNICATION,
    true,
    setNotificationEnableSlotCallback);
```


<a id="setnotificationenableslot-1"></a>

## setNotificationEnableSlot

```TypeScript
function setNotificationEnableSlot(
    bundle: BundleOption,
    type: SlotType,
    enable: boolean,
    isForceControl: boolean,
    callback: AsyncCallback<void>,
  ): void
```

设置指定应用的指定渠道类型的使能状态。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | 是 | 应用的包信息。 |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 指定渠道类型。 |
| enable | boolean | 是 | 使能状态（true：使能，false：禁止）。 |
| isForceControl | boolean | 是 | 渠道开关是否受通知授权开关影响（false：受影响，true：不受影响）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设置渠道使能回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// setNotificationEnableSlot
let setNotificationEnableSlotCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`setNotificationEnableSlot failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info('setNotificationEnableSlot success');
    }
};
notificationManager.setNotificationEnableSlot(
    { bundle: 'ohos.samples.notification', },
    notificationManager.SlotType.SOCIAL_COMMUNICATION,
    true,
    setNotificationEnableSlotCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let setNotificationEnableSlotCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`setNotificationEnableSlot failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info('setNotificationEnableSlot success');
    }
};

notificationManager.setNotificationEnableSlot(
    { bundle: 'ohos.samples.notification', },
    notificationManager.SlotType.SOCIAL_COMMUNICATION,
    true,
    false,
    setNotificationEnableSlotCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// setNotificationEnableSlot
notificationManager.setNotificationEnableSlot(
    { bundle: 'ohos.samples.notification', },
    notificationManager.SlotType.SOCIAL_COMMUNICATION,
    true).then(() => {
        console.info('setNotificationEnableSlot success');
    }).catch((err: BusinessError) => {
        console.error(`setNotificationEnableSlot failed, code is ${err.code}, message is ${err.message}`);
    });
```


<a id="setnotificationenableslot-2"></a>

## setNotificationEnableSlot

```TypeScript
function setNotificationEnableSlot(bundle: BundleOption, type: SlotType, enable: boolean, isForceControl?: boolean): Promise<void>
```

设置指定应用的指定渠道类型的使能状态。使用promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | 是 | 应用的包信息。 |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 渠道类型。 |
| enable | boolean | 是 | 使能状态（true：使能，false：禁止）。 |
| isForceControl | boolean | 否 | 渠道开关是否受通知总开关影响（false：受总开关影响，true：不受总开关影响）。默认为false。<br>**适用版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space.<br>**适用版本：** 11+ |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// setNotificationEnableSlot
notificationManager.setNotificationEnableSlot(
    { bundle: 'ohos.samples.notification', },
    notificationManager.SlotType.SOCIAL_COMMUNICATION,
    true).then(() => {
        console.info('setNotificationEnableSlot success');
    }).catch((err: BusinessError) => {
        console.error(`setNotificationEnableSlot failed, code is ${err.code}, message is ${err.message}`);
    });
```
