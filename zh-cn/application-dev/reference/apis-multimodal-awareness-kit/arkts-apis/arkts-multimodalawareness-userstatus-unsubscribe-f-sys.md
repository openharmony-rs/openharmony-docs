# unsubscribe（系统接口）

## unsubscribe

```TypeScript
function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): int
```

取消订阅用户状态监测。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): int--><!--Device-userStatus-function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 表示要取消订阅的特性。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)&gt; | 否 | 回调函数，返回用户状态数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 操作成功返回0，否则返回非0值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited &lt;br&gt; device capabilities. |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: &lt;br&gt;1. System error, such as a null pointer and container-related exception. &lt;br&gt;2. Node-API invocation exception, such as invalid Node-API status. |
| [33900003](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900003-取消订阅失败) | Unsubscription failed. Possible causes: &lt;br&gt;1. Callback failure. &lt;br&gt;2. Node-API invocation exception, such as invalid Node-API status. &lt;br&gt;3. IPC request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

