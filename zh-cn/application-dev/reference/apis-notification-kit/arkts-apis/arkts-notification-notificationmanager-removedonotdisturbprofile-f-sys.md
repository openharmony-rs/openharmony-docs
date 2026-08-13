# removeDoNotDisturbProfile（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## removeDoNotDisturbProfile

```TypeScript
function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>): Promise<void>
```

删除勿扰模式配置。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>): Promise<void>--><!--Device-notificationManager-function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templates | Array&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | 是 | 勿扰模式的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: '工作模式'
  }
]
notificationManager.removeDoNotDisturbProfile(templates).then(() => {
  console.info('removeDoNotDisturbProfile success.');
}).catch((err: BusinessError) => {
  console.error(`removeDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: '工作模式'
  }
]
notificationManager.removeDoNotDisturbProfile(templates).then(() => {
  console.info('removeDoNotDisturbProfile success.');
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`removeDoNotDisturbProfile failed, code is ${error.code}, message is ${error.message}`);
});
```


## removeDoNotDisturbProfile

```TypeScript
function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>, userId: int): Promise<void>
```

删除指定用户的勿扰模式配置。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>, userId: int): Promise<void>--><!--Device-notificationManager-function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>, userId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templates | Array&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | 是 | 勿扰模式的配置信息。 |
| userId | int | 是 | 删除勿扰模式配置的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId : number = 100;
let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: '工作模式'
  }
]
notificationManager.removeDoNotDisturbProfile(templates, userId).then(() => {
  console.info('removeDoNotDisturbProfile success.');
}).catch((err: BusinessError) => {
  console.error(`removeDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
let userId : int = 100;
let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: '工作模式'
  }
]
notificationManager.removeDoNotDisturbProfile(templates, userId).then(() => {
  console.info(`removeDoNotDisturbProfile success. userId: ${userId}, templates: ${JSON.stringify(templates)}`);
}).catch((err: Error | undefined): void => {
  console.info(`removeDoNotDisturbProfile error, code: ${err?.code}, message: ${err?.message}`);
});
```

