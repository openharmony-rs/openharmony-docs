# getControlledAppLists

## getControlledAppLists

```TypeScript
function getControlledAppLists(): Promise<Array<string>>
```

获取当前用户受企业DLP控制的应用程序列表。使用Promise异步回调。 > **说明：** > > 该接口仅能查询通过 > [setControlledAppLists]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 设置的受企业DLP控制的应用程序列表。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.DLP_POLICY_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dlpPermission-function getControlledAppLists(): Promise<Array<string>>--><!--Device-dlpPermission-function getControlledAppLists(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise that returns the appIdentifiers of controlled application |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getControlledAppLists().then((res) => {
  console.info('res', JSON.stringify(res));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
}).finally(() => {
  console.info("Completed getControlledAppLists operation.");
})
```

