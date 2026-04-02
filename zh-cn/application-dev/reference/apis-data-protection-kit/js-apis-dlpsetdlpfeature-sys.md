# @ohos.dlpSetDlpFeature (设置数据防泄漏入口)(系统接口)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

本模块提供数据防泄漏（Data Loss Prevention，简称为DLP）特性开关的控制能力，包括开启和关闭DLP特性开关、返回特性开关状态设置是否成功等。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块接口为系统接口。

## 导入模块

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
```

## dlpSetDlpFeature.setDlpFeature

setDlpFeature(status: DlpFeatureStatus): Promise&lt;StatusInfoResult&gt;

设置DLP特性开关状态。使用Promise异步回调。

当特性开关处于开启状态时，右键单击可加密文件，菜单中会显示“加密保护”选项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| status | [DlpFeatureStatus](#dlpfeaturestatus) | 是 | DLP特性开关状态。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[StatusInfoResult](#statusinforesult)&gt; | Promise对象，返回DLP特性开关状态设置的结果信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[DLP服务错误码](errorcode-dlp.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | Non-system applications use system APIs. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**示例：**

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

async exampleFunction() {
  try {
    let res: dlpSetDlpFeature.StatusInfoResult =
      await dlpSetDlpFeature.setDlpFeature(dlpSetDlpFeature.DlpFeatureStatus.ENABLED_FEATURE);
    console.info('setDlpFeature result: ', JSON.stringify(res));
  } catch (err) {
    console.error('setDlpFeature failed', (err as BusinessError).code, (err as BusinessError).message);
  }
}
```

## StatusInfoResult

DLP特性开关状态设置的结果信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| isSuccess | boolean | 否 | 否 | DLP特性开关状态是否设置成功。true表示设置成功；false表示设置失败。 |

## DLPFeatureInfo

DLP特性开关的状态信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| dlpFeatureStatus | [DlpFeatureStatus](#dlpfeaturestatus) | 否 | 否 | DLP特性开关的状态。 |

## DlpFeatureStatus

DLP特性开关状态的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NOT_ENABLED_FEATURE | 0 | 表示关闭DLP特性开关。 |
| ENABLED_FEATURE | 1 | 表示开启DLP特性开关。 |
