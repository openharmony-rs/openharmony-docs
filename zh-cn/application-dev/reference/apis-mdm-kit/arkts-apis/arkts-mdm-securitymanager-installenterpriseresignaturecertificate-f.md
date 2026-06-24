# installEnterpriseReSignatureCertificate

## installEnterpriseReSignatureCertificate

```TypeScript
function installEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, fd: number, accountId: number): void
```

��װ��ҵӦ����ǩ��֤�顣

ͬһ�û��������·�10����֤ͬ�顣֤�������Ϊ֤���Ψһ��ʶ����֧���ظ��·���ͬ������֤�顣�������ͬһ������֤�飬���ȵ���
[uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md#uninstallEnterpriseReSignatureCertificate-1)����ж�ء�

��MDMӦ��ж�ػ�adminȡ��������£��Ѱ�װ��֤��ᱣ�����豸�ϣ����ᱻ�Ƴ���

����ҵӦ�÷ַ������£�<!--RP2--><!--RP2End-->�����߿���ʹ����ǩ��֤�����ҵӦ�ý��ж���ǩ����ǩ����ɺ�Ӧ�ð��ṩ����ҵ����Ա����ҵ����Ա���Խ���ǩ�����Ӧ�ð�װ���Ѳ�����ǩ��֤�����ҵ�豸�ϡ�

��ҵӦ����ǩ��֤��ʹ�����̣�<!--RP3--><!--RP3End-->

1.ͨ��MDMӦ�ð�װ��ҵӦ����ǩ��֤�飻

2.����������ǩ�����ߣ���ohos-signer��DevEco Studioǩ�����������ԭʼHAP�����ж���ǩ����

3.��װ��ǩ��Ӧ�ã�����ͨ����ҵ˽��Ӧ���г���װ����

4.����Ӧ�á�

���Լ����

1.��װ�µ�ǩ��֤��֮��ʹ�þ�ǩ��֤���Ӧ�ÿ��Լ������У�

2.�Ѿ���װ����ҵӦ�ã���װ���µ���ҵǩ��֤����Ѱ�װ��Ӧ��������£�����ֱ�Ӹ��ǰ�װ��������ж��ԭӦ�ã�

3.��ҵ�����£��ر������漰��Ϣ��ȫ�ĳ����У���ҵ��Ҫȷ��Ա��ʹ�õ��ƶ��豸�н���װ�������ض����ڲ������͹��ߡ���ҵӦ����ǩ��֤��ͨ��ͳһ��Ӧ�����ݱ�ʶ����ϵͳ��Ӧ�ù�����Ȩ�޿��ƻ������ʹ�ã���֧����ҵӦ�õľ�Ĭ��װ���ܿص�ϵͳ
�������ü����з�Χ���ƣ��Ӷ�ʵ����ҵ�������ܿ��ն��ϵ�׼������밲ȫ������

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| certificateAlias | string | 是 | ֤�������������'.cer'��β�� |
| fd | number | 是 | ��ʾ�Ѵ��ڵ���ǩ��֤���ļ���������֤���ļ���Ҫ������[Ӧ��ɳ��Ŀ¼](../../../../file-management/app-sandbox-directory.md)�� |
| accountId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ��*@ohos.account.osAccount** to obtain the account ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201006](../../errorcode-universal.md#9201006-The) | The number of certificates has reached the limit. |
| [9201007](../../errorcode-universal.md#9201007-The) | The certificate is invalid. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

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

