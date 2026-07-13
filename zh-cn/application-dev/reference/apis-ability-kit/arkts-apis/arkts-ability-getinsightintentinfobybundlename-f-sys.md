# getInsightIntentInfoByBundleName（系统接口）

## getInsightIntentInfoByBundleName

```TypeScript
function getInsightIntentInfoByBundleName(bundleName: string, intentFlags: number): Promise<Array<InsightIntentInfo>>
```

根据包名查询当前设备上的意图信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名称。 <br/>**说明：**<br/> 若包名不存在，则返回空数组。 |
| intentFlags | number | 是 | 意图信息（[InsightIntentInfo](arkts-ability-insightintentinfo-i-sys.md)）的标识，用于表示查询全量意图信息或者简要意图信息，参考[GetInsightIntentFlag](arkts-ability-getinsightintentflag-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;InsightIntentInfo&gt;&gt; | Promise对象，返回意图信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service;2. The system service fails to communicate with the dependency module. |

