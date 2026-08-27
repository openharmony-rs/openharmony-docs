# off（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## off('continueStateChange')

```TypeScript
function off(type: 'continueStateChange', callback?: Callback<ContinueCallbackInfo>): void
```

取消当前任务流转的状态监听。此接口需与on('continueStateChange')成对使用，在不需要监听时应及时调用以释放资源。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continueStateChange' | 是 | 取消订阅的事件类型，固定取值为'continueStateChange'，表示取消订阅任务流转状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md)&gt; | 否 | 需要取消的回调函数。当需要取消特定回调监听时传入callback参数，当需要取消type对应的所有回调监听时不传callback参数。不传入时将取消该事件类型的所有回调监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';

  try {
    // 取消任务流转状态变化事件监听
    distributedMissionManager.off('continueStateChange', (data) => {
      console.info("continueStateChange off:" + JSON.stringify(data));
    });
  } catch (err) {
    console.error(`continueStateChange failed. Code: ${err.code}, message: ${err.message}`);
  }
```
