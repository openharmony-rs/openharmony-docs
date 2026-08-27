# on（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## on('continueStateChange')

```TypeScript
function on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>): void
```

注册当前任务流转状态的监听。此接口需与off('continueStateChange')成对使用，不再监听时应及时取消；调用顺序为先通过on注册监听，不需要时再调用off取消监听。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continueStateChange' | 是 | 订阅的事件类型，取值为'continueStateChange'，表示订阅任务流转状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md)&gt; | 是 | 回调函数，返回当前任务的流转状态和流转信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

  try {
    // 注册任务流转状态变化事件监听
    distributedMissionManager.on('continueStateChange', (data) => {
      console.info("continueStateChange on:" + JSON.stringify(data));
    });
  } catch (error) {
    console.error(`continueStateChange failed. Code: ${error.code}, message: ${error.message}`);
  }
```
