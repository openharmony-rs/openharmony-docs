# installEnterpriseReSignatureCertificate

## installEnterpriseReSignatureCertificate

```TypeScript
function installEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, fd: number, accountId: number): void
```

安装企业应用重签名证书。

同一用户下最多可下发10本不同证书。证书别名作为证书的唯一标识，不支持重复下发相同别名的证书。如需更新同一别名的证书，需先调用
[uninstallEnterpriseReSignatureCertificate](arkts-mdm-uninstallenterpriseresignaturecertificate-f.md#uninstallenterpriseresignaturecertificate-1)进行卸载。

在MDM应用卸载或admin取消激活场景下，已安装的证书会保留在设备上，不会被移除。

在企业应用分发场景下，<!--RP2--><!--RP2End-->开发者可以使用重签名证书对企业应用进行二次签名，签名完成后将应用包提供给企业管理员。企业管理员可以将重签名后的应用安装在已部署重签名证书的企业设备上。

企业应用重签名证书使用流程：<!--RP3--><!--RP3End-->

1.通过MDM应用安装企业应用重签名证书；

2.开发者利用签名工具（如ohos-signer或DevEco Studio签名插件），对原始HAP包进行二次签名；

3.安装重签名应用（可以通过企业私有应用市场安装）；

4.运行应用。

规格约束：

1.安装新的签名证书之后，使用旧签名证书的应用可以继续运行；

2.已经安装的企业应用，安装了新的企业签名证书后，已安装的应用如需更新，可以直接覆盖安装，无需先卸载原应用；

3.企业场景下，特别是在涉及信息安全的场景中，企业需要确保员工使用的移动设备中仅安装并运行特定的内部软件和工具。企业应用重签名证书通过统一的应用身份标识，与系统的应用管理与权限控制机制配合使用，可支持企业应用的静默安装、受控的系统
能力调用及运行范围限制，从而实现企业软件在受控终端上的准入控制与安全管理。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| certificateAlias | string | 是 | 证书别名，必须以'.cer'结尾。 |
| fd | number | 是 | 表示已存在的重签名证书文件描述符，证书文件需要放置于[应用沙箱目录](../../../../file-management/app-sandbox-directory.md)。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。*@ohos.account.osAccount** to obtain the account ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201006](../errorcode-enterpriseDeviceManager.md#9201006-安装企业重签名证书超过数量上限) | The number of certificates has reached the limit. |
| [9201007](../errorcode-enterpriseDeviceManager.md#9201007-企业重签名证书无效) | The certificate is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// test.cer证书文件需要放置在应用沙箱目录下，并确保是有效的企业应用重签名证书
// 需根据实际情况进行替换
const filePath = '/test.cer';
// 需根据实际情况进行替换
let certificateAlias: string = 'test.cer';
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_ONLY).fd;
// 需根据实际情况进行替换
let accountId: number = 100;
try {
  securityManager.installEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, fd, accountId);
  console.info('Success to install enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to install enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};

```

