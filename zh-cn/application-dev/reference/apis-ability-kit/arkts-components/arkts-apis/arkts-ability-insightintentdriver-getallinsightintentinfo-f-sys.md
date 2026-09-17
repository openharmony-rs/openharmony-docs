# getAllInsightIntentInfo（系统接口）

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## getAllInsightIntentInfo

```TypeScript
function getAllInsightIntentInfo(intentFlags: number): Promise<Array<InsightIntentInfo>>
```

查询当前设备上的所有意图信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intentFlags | number | 是 | 意图信息（[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md)）的标识，用于表示查询全量意图信息或者简要意图信息，参考[GetInsightIntentFlag](arkts-ability-insightintentdriver-getinsightintentflag-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md)&gt;&gt; | Promise对象，返回意图信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service fails to communicate with the dependency module. |

**示例**

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function getInfos() {
    try {
      insightIntentDriver.getAllInsightIntentInfo(insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO).then((data) => {
        hilog.info(0x0000, 'testTag', 'getAllInsightIntentInfo return %{public}s', JSON.stringify(data));
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo errMessage: %{public}s', err.message);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo error caught %{public}s', JSON.stringify(error));
    }
  }
```
