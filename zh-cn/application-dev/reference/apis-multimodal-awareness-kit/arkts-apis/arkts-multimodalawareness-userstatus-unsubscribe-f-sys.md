# unsubscribe（系统接口）

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## unsubscribe

```TypeScript
function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): number
```

取消订阅用户状态监控。与subscribe()方法成对使用，用于取消订阅回调并释放资源。必须在subscribe()之后调用，取消未订阅的featureId返回失败。 <br>建议在应用退出或不再需要监控时调用unsubscribe()。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): number--><!--Device-userStatus-function unsubscribe(featureId: UserStatusFeature, callback?: Callback<UserStatusData>): number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 表示要取消订阅的用户状态检测功能类型。对应subscribe时传入的featureId值。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)&gt; | 否 | 表示取消指定的callback回调函数。如果输入空、undefined或null，则取消featureId订阅的所有通知事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回执行结果。返回0表示操作成功，非零值表示操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited <br> device capabilities. |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| [33900003](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900003-取消订阅失败) | Unsubscription failed. Possible causes: <br>1. Callback failure. <br>2. Node-API invocation exception, such as invalid Node-API status. <br>3. IPC request exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

