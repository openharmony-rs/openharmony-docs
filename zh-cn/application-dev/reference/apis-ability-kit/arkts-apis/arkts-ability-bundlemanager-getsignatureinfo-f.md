# getSignatureInfo

## getSignatureInfo

```TypeScript
function getSignatureInfo(uid: int): SignatureInfo
```

根据给定的uid获取对应应用的[签名信息]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_SIGNATURE_INFO

<!--Device-bundleManager-function getSignatureInfo(uid: int): SignatureInfo--><!--Device-bundleManager-function getSignatureInfo(uid: int): SignatureInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示应用程序的UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回SignatureInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700021](../errorcode-bundle.md#17700021-指定的uid无效) | The uid is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005; // uid需要替换为对应应用程序的UID。
try {
  let data = bundleManager.getSignatureInfo(uid);
  hilog.info(0x0000, 'testTag', 'getSignatureInfo successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSignatureInfo failed. Cause: %{public}s', message);
}
```

