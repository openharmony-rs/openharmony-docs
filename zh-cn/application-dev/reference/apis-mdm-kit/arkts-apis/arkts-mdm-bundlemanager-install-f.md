# install

## install

```TypeScript
function install(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

��װָ��·���µ�Ӧ�ð���ʹ��Promise�첽�ص���</br>�˽ӿ�ֻ�ܰ�װ�ַ�����Ϊenterprise_mdm��MDMӦ�ã���enterprise_normal����ͨ��ҵӦ�ã����͵�Ӧ�ã�����ͨ��
[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)�ӿڲ�ѯӦ��
������[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md#BundleInfo)������BundleInfo.appInfo.appDistributionTypeΪӦ�õķַ����͡�

> **˵����**
>
> �ýӿڱȽϺ�ʱ�������ô˽ӿں󣬺��������Ӧ�����̵߳�������ͬ���ӿ�ʱ��Ҫ�ȴ��ýӿ��첽���ء�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| hapFilePaths | Array&lt;string&gt; | 是 | ����װӦ�ð�·�����顣Ӧ�ð�·��ΪӦ��ɳ��·��(Ӧ��ɳ��·������ʵ·���Ķ�Ӧ��ϵ�ɲμ���<br/>[Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ](../../../../file-management/app-sandbox-directory.md#Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ))��Ӧ����Ȩ�޷��ʵ�·���� |
| installParam | InstallParam | 否 | Ӧ�ð���װ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�Ӧ�ó������װʧ��ʱ���׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201002](../../errorcode-universal.md#9201002-Failed) | Failed to install the application. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 为当前用户安装应用
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let hapFilePaths: Array<string> = ['/data/storage/el2/base/haps/entry/testinstall/ExtensionTest.hap'];

bundleManager.install(wantTemp, hapFilePaths).then(() => {
  console.info('Succeeded in installing bundles.');
}).catch((err: BusinessError) => {
  console.error(`Failed to install bundles. Code is ${err.code}, message is ${err.message}`);
});

```

```TypeScript
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 为所有用户安装应用
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let hapFilePaths: Array<string> = ['/data/storage/el2/base/haps/entry/testinstall/ExtensionTest.hap'];
const params: Record<string, string> = {
  'ohos.bms.param.enterpriseForAllUser': 'true'
};
let installParam: bundleManager.InstallParam = {
  // 需根据实际情况进行替换
  userId: 100,
  installFlag: 0,
  parameters: params
};
bundleManager.install(wantTemp, hapFilePaths, installParam).then(() => {
  console.info('Succeeded in installing bundles.');
}).catch((err: BusinessError) => {
  console.error(`Failed to install bundles. Code is ${err.code}, message is ${err.message}`);
});

```

