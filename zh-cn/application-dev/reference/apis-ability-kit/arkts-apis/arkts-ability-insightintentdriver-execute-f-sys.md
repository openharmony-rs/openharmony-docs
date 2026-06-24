# execute（系统接口）

## execute

```TypeScript
function execute(param: ExecuteParam, callback: AsyncCallback<insightIntent.ExecuteResult>): void
```

执行意图调用的接口。使用callback异步回调。
当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。
当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要
申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。

**起始版本：** 11

**需要权限：** ohos.permission.EXECUTE_INSIGHT_INTENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | ExecuteParam | 是 | 执行意图调用的参数。 |
| callback | AsyncCallback&lt;insightIntent.ExecuteResult&gt; | 是 | 回调函数，返回意图调用执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16000137](../../errorcode-universal.md#16000137-Crossdevice) | Cross-device execution failed due to a connection error.&lt;br&gt;**适用版本：** 26.0.0+ |
| [16000138](../../errorcode-universal.md#16000138-Device) | Device disconnected during cross-device intent execution.&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
  import { insightIntentDriver, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  function executeInsightIntentAsync() {
    let param: insightIntentDriver.ExecuteParam = {
      bundleName: 'com.ohos.intentexecutedemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      insightIntentName: 'PlayMusic',
      insightIntentParam: {
        songName: 'City Of Stars',
      },
      executeMode: insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND,
    };

    try {
      insightIntentDriver.execute(param, (error, data: insightIntent.ExecuteResult) => {
        if (error) {
          hilog.error(0x0000, 'testTag', 'execute insight intent failed with %{public}s', JSON.stringify(error));
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'execute insight intent succeed');
        }
        hilog.info(0x0000, 'testTag', 'execute insight intent return %{public}d', data.code);
        hilog.info(0x0000, 'testTag', 'execute insight intent result %{public}s', JSON.stringify(data.result));
      })
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'execute insight intent error caught %{public}s', JSON.stringify(error));
    }
  }

```


## execute

```TypeScript
function execute(param: ExecuteParam): Promise<insightIntent.ExecuteResult>
```

执行意图调用的接口。使用Promise异步回调。
当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。
当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要
申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。

**起始版本：** 11

**需要权限：** ohos.permission.EXECUTE_INSIGHT_INTENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | ExecuteParam | 是 | 执行意图调用的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;insightIntent.ExecuteResult&gt; | Promise used to return the intent call execution result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16000137](../../errorcode-universal.md#16000137-Crossdevice) | Cross-device execution failed due to a connection error.&lt;br&gt;**适用版本：** 26.0.0+ |
| [16000138](../../errorcode-universal.md#16000138-Device) | Device disconnected during cross-device intent execution.&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
  import { insightIntentDriver, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeSearchMusicIntentPromise() {
    let param: insightIntentDriver.ExecuteParam = {
      bundleName: 'com.ohos.intentexecutedemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      insightIntentName: 'PlayMusic',
      insightIntentParam: {
        songName: 'City Of Stars',
      },
      executeMode: insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND,
    };

    try {
      let resultData: insightIntent.ExecuteResult = await insightIntentDriver.execute(param);
      hilog.info(0x0000, 'testTag', 'execute insight intent return %{public}d', resultData.code);
      hilog.info(0x0000, 'testTag', 'execute insight intent result %{public}s', JSON.stringify(resultData.result));
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'execute insight intent error caught %{public}s', JSON.stringify(error));
    }
  }

```

