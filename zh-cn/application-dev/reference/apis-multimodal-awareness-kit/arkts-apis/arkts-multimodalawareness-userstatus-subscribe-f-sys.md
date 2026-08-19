# subscribe（系统接口）

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## subscribe

```TypeScript
function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,
    deviceInfo?: DeviceInfo[]): number
```

订阅用户状态监控，以获取用户状态数据。调用subscribe()后，必须在使用完毕后调用unsubscribe()取消订阅以释放回调资源，未调用unsubscribe()会导致回调资源泄漏， <br>影响应用性能。建议先调用configure()配置功能参数，再调用subscribe()开始订阅。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,    deviceInfo?: DeviceInfo[]): number--><!--Device-userStatus-function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,    deviceInfo?: DeviceInfo[]): number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 表示用户状态检测功能类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)&gt; | 是 | 回调函数，用于接收用户状态数据。当订阅的用户状态数据更新时会被调用。 |
| deviceInfo | DeviceInfo[] | 否 | 表示要开启用户状态监控的设备列表。当featureId为HAND_GAZE_COORDINATION时需要输入有效且非空的deviceInfo信息， <br>否则影响功能使用；其他featureId可省略此参数。如果输入空、undefined或null，则认为没有传入实际值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回注册的回调ID。唯一标识对应回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited <br> device capabilities. |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: <br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as a invalid Node-API status. |
| [33900002](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900002-订阅失败) | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

