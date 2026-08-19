# offContinueStateChange（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## offContinueStateChange

```TypeScript
function offContinueStateChange(callback?: Callback<ContinueCallbackInfo>): void
```

Continue mission

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function offContinueStateChange(callback?: Callback<ContinueCallbackInfo>): void--><!--Device-distributedMissionManager-function offContinueStateChange(callback?: Callback<ContinueCallbackInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md)&gt; | 否 | The callback of continueStateChange. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

