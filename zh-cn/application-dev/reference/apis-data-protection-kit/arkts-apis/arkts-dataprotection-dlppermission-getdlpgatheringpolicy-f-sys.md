# getDLPGatheringPolicy（系统接口）

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getDLPGatheringPolicy

```TypeScript
function getDLPGatheringPolicy(): Promise<GatheringPolicyType>
```

查询DLP沙箱聚合策略。使用Promise异步回调。

应用需要获取当前系统的DLP沙箱聚合策略配置时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function getDLPGatheringPolicy(): Promise<GatheringPolicyType>--><!--Device-dlpPermission-function getDLPGatheringPolicy(): Promise<GatheringPolicyType>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<GatheringPolicyType> | Promise对象。返回当前DLP沙箱聚合策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPGatheringPolicy().then((gatheringPolicy: dlpPermission.GatheringPolicyType) => {
  console.info('gatheringPolicy: ', JSON.stringify(gatheringPolicy));
}).catch((error: BusinessError)=> {
  console.error(error.message);
}); // 获取沙箱聚合策略。

```


## getDLPGatheringPolicy

```TypeScript
function getDLPGatheringPolicy(callback: AsyncCallback<GatheringPolicyType>): void
```

查询DLP沙箱聚合策略。使用callback异步回调。

应用需要获取当前系统的DLP沙箱聚合策略配置时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function getDLPGatheringPolicy(callback: AsyncCallback<GatheringPolicyType>): void--><!--Device-dlpPermission-function getDLPGatheringPolicy(callback: AsyncCallback<GatheringPolicyType>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<GatheringPolicyType> | 是 | 回调函数。err为undefined时表示查询成功；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPGatheringPolicy((err, gatheringPolicy) => {
  if (err !== undefined) {
    console.error('getDLPGatheringPolicy error,', err.code, err.message);
  } else {
    console.info('gatheringPolicy：', JSON.stringify(gatheringPolicy));
  }
}); // 获取沙箱聚合策略。

```

