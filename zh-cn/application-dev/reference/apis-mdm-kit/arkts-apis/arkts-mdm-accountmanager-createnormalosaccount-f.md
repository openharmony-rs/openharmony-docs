# createNormalOsAccount

## createNormalOsAccount

```TypeScript
function createNormalOsAccount(admin: Want, name: string): Promise<osAccount.OsAccountInfo>
```

创建普通系统账号。最多可以创建2个normal类型的系统账号 ([osAccount.OsAccountType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_) 。 > **说明：** > > 创建账号的流程比较耗时，当调用此接口后，后续如果在应用主线程调用其他同步接口时需要等待该接口异步返回。 > > 创建系统账号对设备的性能影响较大，此接口仅支持12GB及以上运行内存的手机、平板设备使用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function createNormalOsAccount(admin: Want, name: string): Promise<osAccount.OsAccountInfo>--><!--Device-accountManager-function createNormalOsAccount(admin: Want, name: string): Promise<osAccount.OsAccountInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| name | string | 是 | 系统账号名称。系统账号名称不能重复且不能为空，会报错误码9200012。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;osAccount.OsAccountInfo&gt; | Promise对象，返回创建的系统账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201003](../errorcode-enterpriseDeviceManager.md#9201003-创建账号失败) | Failed to add an OS account. |
| [9201040](../errorcode-enterpriseDeviceManager.md#9201040-系统账号数量已达到最大限制) | The number of accounts reaches the upper limit. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { osAccount } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 创建普通系统账号，需要传入账号名称
accountManager.createNormalOsAccount(wantTemp, "TestAccountName").then((accountInfo: osAccount.OsAccountInfo) => {
  console.info('Succeeded in creating normal os account, accountInfo: ' + JSON.stringify(accountInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to create normal os account: code is ${err.code}, message is ${err.message}`);
});
```

