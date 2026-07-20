# on（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

<a id="on"></a>
## on('continueStateChange')

```TypeScript
function on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>): void
```

注册当前任务流转状态的监听。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>): void--><!--Device-distributedMissionManager-function on(type: 'continueStateChange', callback: Callback<ContinueCallbackInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continueStateChange' | 是 | 当前任务流转状态，取值为'continueStateChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ContinueCallbackInfo&gt; | 是 | 回调函数，返回当前任务的流转状态和流转信息。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

