# @ohos.dlpSetDlpFeature (设置数据防泄漏入口)(系统接口)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

本模块提供数据防泄漏（DLP）入口控制能力，包括开启和关闭DLP入口、返回入口状态设置是否成功等，可通过[setDlpFeature](#dlpSetDlpFeature.setDlpFeature)接口实现。

**起始版本：** 26.0.0

> **说明：**
>
> - 本模块为系统接口。

## 导入模块

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
```

## dlpSetDlpFeature.setDlpFeature

setDlpFeature(status: DlpFeatureStatus): Promise&lt;StatusInfoResult&gt;

设置DLP入口状态。使用Promise方式异步返回结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| status | [DlpFeatureStatus](#dlpfeaturestatus) | 是 | DLP入口状态。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[StatusInfoResult](#statusinforesult)&gt; | Promise对象。返回DLP入口状态设置结果的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[DLP服务错误码](errorcode-dlp.md)。

| 错误码ID | 错误信息（此处仅提供错误抛出的关键信息） |
| -------- | -------- |
| 202 | Non-system applications use system APIs. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**示例：**

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

async ExampleFunction() {
	try {
		let res: dlpSetDlpFeature.StatusInfoResult =
			await dlpSetDlpFeature.setDlpFeature(dlpSetDlpFeature.DlpFeatureStatus.ENABLED_FEATURE);
		console.info('setDlpFeature result:', JSON.stringify(res));
	} catch (err) {
		console.error('setDlpFeature failed', (err as BusinessError).code, (err as BusinessError).message);
	}
}
```

## StatusInfoResult

表示DLP入口状态设置结果的信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| isSuccess | boolean | 否 | 否 | DLP入口状态是否设置成功。 |

## DlpFeatureStatus

表示DLP入口状态的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NOT_ENABLED_FEATURE | 0 | 表示关闭DLP入口。 |
| ENABLED_FEATURE | 1 | 表示开启DLP入口。 |

## DLPFeatureInfo

表示DLP功能状态的信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.DataLossPrevention

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| dlpFeatureStatus | [DlpFeatureStatus](#dlpfeaturestatus) | 否 | 否 | DLP入口状态。 |
