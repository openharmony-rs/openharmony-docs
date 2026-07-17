# getInsightIntentInfoByFilter（系统接口）

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## getInsightIntentInfoByFilter

```TypeScript
function getInsightIntentInfoByFilter(filter: InsightIntentInfoFilter): Promise<Array<InsightIntentInfo>>
```

Obtains the intent information on the current device based on the given intent filter. This API uses a promise to return the result.<br>If the user ID of the calling application is different from the user ID of the intent, the

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-insightIntentDriver-function getInsightIntentInfoByFilter(filter: InsightIntentInfoFilter): Promise<Array<InsightIntentInfo>>--><!--Device-insightIntentDriver-function getInsightIntentInfoByFilter(filter: InsightIntentInfoFilter): Promise<Array<InsightIntentInfo>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [InsightIntentInfoFilter](arkts-ability-insightintentdriver-insightintentinfofilter-i-sys.md) | 是 | Intent filter, which specifies the criteria for selecting a target intent. It is used to filter intents on the device that meet these criteria. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InsightIntentInfo>> | Promise used to return an array holding InsightIntentInfo objects. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**示例：**

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function getInfoByFilter() {
  let filter: insightIntentDriver.InsightIntentInfoFilter = {
    intentFlags: insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO,
    bundleName: 'com.example.intent', // 开发者需自行修改为实际包名
    moduleName: 'entry', // 开发者需自行修改为实际模块名
    intentName: 'PlayMusic', // 开发者需自行修改为实际意图名
    userId: 100, // 开发者需自行修改为实际userId
  };

  try {
    insightIntentDriver.getInsightIntentInfoByFilter(filter).then((data) => {
      hilog.info(0x0000, 'testTag', 'getInsightIntentInfoByFilter return %{public}s', JSON.stringify(data));
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter errCode: %{public}d', err.code);
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter errMessage: %{public}s', err.message);
    });
  } catch (error) {
    hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter error caught %{public}s', JSON.stringify(error));
  }
}

```

