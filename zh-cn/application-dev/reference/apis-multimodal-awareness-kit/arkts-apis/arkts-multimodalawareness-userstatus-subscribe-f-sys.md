# subscribe（系统接口）

## subscribe

```TypeScript
function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,
    deviceInfo?: DeviceInfo[]): int
```

订阅用户状态监测。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,    deviceInfo?: DeviceInfo[]): int--><!--Device-userStatus-function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,    deviceInfo?: DeviceInfo[]): int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 表示要订阅的特性。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)&gt; | 是 | 回调函数，返回用户状态数据。 |
| deviceInfo | DeviceInfo[] | 否 | 启用用户状态监测的设备列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回已注册的回调ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited &lt;br&gt; device capabilities. |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: &lt;br&gt;1. System error, such as null pointer and container-related exception. &lt;br&gt;2. Node-API invocation exception, such as a invalid Node-API status. |
| [33900002](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900002-订阅失败) | Subscription failed. Possible causes: &lt;br&gt;1. Callback registration failed. &lt;br&gt;2. Failed to bind the native object to the JS wrapper. &lt;br&gt;3. Node-API invocation exception, such as invalid Node-API status. &lt;br&gt;4. IPC request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

