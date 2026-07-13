# setDlpFeature（系统接口）

## setDlpFeature

```TypeScript
function setDlpFeature(status: DlpFeatureStatus): Promise<StatusInfoResult>
```

设置DLP特性开关状态。使用Promise异步回调。调用成功后，DLP特性开关将设置为指定状态，系统将根据该状态启用或禁用DLP保护功能。

当特性开关处于开启状态时，右键单击支持加密的文件，右键菜单中会显示“加密保护”选项。可加密类型包括：.txt，.pdf，.xls，.xlsx，.ppt，.pptx，.doc，.docx。

企业策略开启或关闭数据防泄漏功能时使用此接口。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | DlpFeatureStatus | 是 | DLP特性开关状态。ENABLED_FEATURE用于开启DLP特性，菜单中显示"加密保护"选项；NOT_ENABLED_FEATURE用于关闭DLP特性，菜单中不显示"加密保护"选项。超出此范围抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;StatusInfoResult&gt; | Promise对象。设置DLP特性开关状态，返回DLP特性开关状态设置的结果信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';

async function exampleFunction() {
  let statusInfoResult: dlpSetDlpFeature.StatusInfoResult =
    await dlpSetDlpFeature.setDlpFeature(dlpSetDlpFeature.DlpFeatureStatus.ENABLED_FEATURE); // 记录执行结果
  console.info('setDlpFeature result: ', JSON.stringify(statusInfoResult));
} // 设置DLP特性开关状态。

exampleFunction();

```

