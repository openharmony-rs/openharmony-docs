# configure（系统接口）

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## configure

```TypeScript
function configure(featureId: UserStatusFeature, detail: string): number
```

配置功能参数。调用成功后，将更新指定功能的配置参数，影响后续该功能的检测行为，如检测灵敏度、采样频率、启用的检测项等。建议在subscribe()之前调用configure()配置功能参数， <br>确保配置在订阅时生效。对于需要特定配置的功能（如USER_MOOD的实时/非实时模式），建议先configure()再subscribe()。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): number--><!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 表示要配置的用户状态检测功能类型。 |
| detail | string | 是 | 配置参数，JSON格式字符串。包含params数组，每个参数包含description（参数名）和value（参数值数组）字段。 <br>具体格式和取值参见下方detail定义说明表格。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回配置执行结果。返回0表示操作成功，非零值表示操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

