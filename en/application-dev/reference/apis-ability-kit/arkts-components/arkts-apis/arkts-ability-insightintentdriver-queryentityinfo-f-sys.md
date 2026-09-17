# queryEntityInfo (System API)

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## queryEntityInfo

```TypeScript
function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>
```

Query insight intent entity information.

**Since:** 26.0.0

**Required permissions:** ohos.permission.EXECUTE_INSIGHT_INTENT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | Yes | Query parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;Record&lt;string, Object&gt;&gt;&gt; | Returns the insight intent entity information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Examples**

```TypeScript
import { insightIntent, insightIntentDriver } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function queryEntityInfoByPromise() {
  let queryParam: insightIntentDriver.QueryParam = {
    bundleName: 'com.example.intent', // Modify it to the actual bundle name.
    moduleName: 'entry', // Modify it to the actual module name.
    intentName: 'PlayMusic', // Modify it to the actual intent name.
    className: 'AppIntentEntityImpl', // Modify it to the actual class name.
    queryEntityParam: {
      queryType: insightIntent.QueryType.BY_PROPERTY,
      parameters: { // Modify it to the actual query parameters.
        'entityId': 'default'
      },
    },
    userId: 100,
  }

  try {
    insightIntentDriver.queryEntityInfo(queryParam)
      .then((data: Array<Record<string, Object>> | undefined) => {
        if (data) {
          hilog.info(0x0000, 'testTag', 'queryEntityInfo return %{public}s', JSON.stringify(data));
        } else {
          hilog.info(0x0000, 'testTag', 'queryEntityInfo return empty result');
        }
      })
      .catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'queryEntityInfo errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'queryEntityInfo errMessage %{public}s', err.message);
      });
  } catch (error) {
    hilog.error(0x0000, 'testTag', 'queryEntityInfo error caught %{public}s', JSON.stringify(error));
  }
}
```
