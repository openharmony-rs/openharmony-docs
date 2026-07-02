# Interface (Notification)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->


用于接收相机通知信息的接口类。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```
## onNotificationReceive

onNotificationReceive(callback: Callback\<NotificationInfo\>): void;

注册接收通知信息的回调，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型                   | 必填 | 说明               |
| -------- | -------------------- | ---- | -------------------- |
| callback | [NotificationInfo](arkts-apis-camera-t.md#notificationinfo) | 是 | 回调函数，返回当前通知信息。 |

**示例：**

```ts
function RegisterNotificationReceive(session: camera.PhotoSession): void {
    session.onNotificationReceive((info: camera.NotificationInfo) => {
        // 监听信息回调，name为信息事件类型，value为信息事件状态。
        console.info(`notification name: ${info.name}, value: ${info.value}.`);
    })
}
```

## offNotificationReceive

offNotificationReceive(callback?: Callback\<NotificationInfo\>): void;

注销接收通知信息的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型                   | 必填 | 说明               |
| -------- | -------------------- | ---- | -------------------- |
| callback | [NotificationInfo](arkts-apis-camera-t.md#notificationinfo) | 否 | 回调函数，返回当前通知信息。如果指定参数则取消对应callback，callback对象如果为空或为匿名函数，则取消所有callback。 |

**示例：**

```ts
function UnregisterNotificationReceive(session: camera.PhotoSession): void {
    session.offNotificationReceive();
}
```