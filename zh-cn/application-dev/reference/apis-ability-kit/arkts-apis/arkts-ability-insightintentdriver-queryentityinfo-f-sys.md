# queryEntityInfo（系统接口）

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## queryEntityInfo

```TypeScript
function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>
```

查询意图实体信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.EXECUTE_INSIGHT_INTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>--><!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | 是 | 查询参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Record&lt;string, Object&gt;&gt;&gt; | - Returns the insight intent entity information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**示例：**

```TypeScript
import { insightIntent, insightIntentDriver } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function queryEntityInfoByPromise() {
  let queryParam: insightIntentDriver.QueryParam = {
    bundleName: 'com.example.intent', // 开发者需自行修改为实际包名
    moduleName: 'entry', // 开发者需自行修改为实际模块名
    intentName: 'PlayMusic', // 开发者需自行修改为实际意图名
    className: 'AppIntentEntityImpl', // 开发者需自行修改为实际的类名
    queryEntityParam: {
      queryType: insightIntent.QueryType.BY_PROPERTY,
      parameters: { // 开发者需自行修改为实际的查询参数
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

