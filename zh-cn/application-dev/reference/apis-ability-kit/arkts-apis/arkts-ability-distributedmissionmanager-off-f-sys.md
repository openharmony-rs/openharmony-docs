# off（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

<a id="off"></a>
## off('continueStateChange')

```TypeScript
function off(type: 'continueStateChange', callback?: Callback<ContinueCallbackInfo>): void
```

取消当前任务流转的状态监听。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function off(type: 'continueStateChange', callback?: Callback<ContinueCallbackInfo>): void--><!--Device-distributedMissionManager-function off(type: 'continueStateChange', callback?: Callback<ContinueCallbackInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continueStateChange' | 是 | 当前任务流转状态，取值为'continueStateChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ContinueCallbackInfo&gt; | 否 | 需要取消的回调函数。<br>参数不填写，取消type对应的所有回调监听。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

