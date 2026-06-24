# notifyUpdatePackages

## notifyUpdatePackages

```TypeScript
function notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise<void>
```

֪ͨϵͳ���°���Ϣ���������������£���Ҫ�ȵ��øýӿ�֪ͨϵͳ���°����ٵ���[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setOtaUpdatePolicy-1)��������
���ԡ�ʹ��Promise�첽�ص���

> **˵����**
>
> �ýӿڱȽϺ�ʱ�������ô˽ӿں󣬺��������Ӧ�����̵߳�������ͬ���ӿ�ʱ��Ҫ�ȴ��ýӿ��첽���ء�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| packageInfo | UpdatePackageInfo | 是 | ϵͳ���°���Ϣ��<br/>**˵����** �����UpdatePackageInfo.packages.path�����ǡ�update����ͷ��zip<br/>ѹ����������������ʽ���ļ��ᱨ9201004�����롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�֪ͨϵͳ���°�ʧ��ʱ���׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201004](../../errorcode-universal.md#9201004-The) | The update packages do not exist or analyzing failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let notify: systemManager.NotifyDescription = {
  // 需根据实际情况进行替换
  "installTips": "installTips",
  "installTipsDetail": "installTips detail"
};
let description: systemManager.PackageDescription = {
  // 需根据实际情况进行替换
  "notify": notify
};
let updatePackages: Array<systemManager.Package> = [];
// 应用沙箱路径，需根据实际情况进行替换
let fileDir = "/xxxx/xxxx/";
let path1: string = "update_sd_base.zip";
let path2: string = "update_sd_cust_xxxxx_all_cn.zip";
let path3: string = "update_sd_preload_xxxxx_all_cn_R1.zip";
let fd1: number = fs.openSync(fileDir + path1, fs.OpenMode.READ_ONLY).fd;
let fd2: number = fs.openSync(fileDir + "xxxxx/" + path2, fs.OpenMode.READ_ONLY).fd;
let fd3: number = fs.openSync(fileDir + "xxxxx/" + path3, fs.OpenMode.READ_ONLY).fd;
let package1: systemManager.Package = {
  // 需根据实际情况进行替换
  "type": systemManager.PackageType.FIRMWARE,
  "path": path1,
  "fd": fd1
};
let package2: systemManager.Package = {
  // 需根据实际情况进行替换
  "type": systemManager.PackageType.FIRMWARE,
  "path": path2,
  "fd": fd2
};
let package3: systemManager.Package = {
  // 需根据实际情况进行替换
  "type": systemManager.PackageType.FIRMWARE,
  "path": path3,
  "fd": fd3
};
updatePackages.push(package1);
updatePackages.push(package2);
updatePackages.push(package3);
let updatePackageInfo: systemManager.UpdatePackageInfo = {
  // 需根据实际情况进行替换
  "version" : "1.0",
  "packages" : updatePackages,
  "description" : description
};
systemManager.notifyUpdatePackages(wantTemp, updatePackageInfo).then(() => {
  console.info('Succeeded in notifying update packages.');
}).catch ((error: BusinessError) => {
  console.error(`Failed to notify update packages. Code is ${error.code},message is ${error.message}`);
});

```

