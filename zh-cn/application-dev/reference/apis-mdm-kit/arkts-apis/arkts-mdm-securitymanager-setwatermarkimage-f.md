# setWatermarkImage

## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void
```

Ϊָ���û���ָ��Ӧ������ˮӡ���ԡ���ǰֻ֧����ౣ��100�����ԡ�

> **˵����**
>
> ���ӿ���������ҵ������Ϊ����Ӧ������ˮӡ��������ҵ��Ϣй¶���ա�������ΪϵͳӦ������ˮӡ���磺����Ӧ�ã������ܴ���δ֪�쳣��

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ������ˮӡ��Ӧ�ð����� |
| source | string \| image.PixelMap | 是 | string��ʾͼ��·����ͼ��·��ΪӦ��ɳ��·��(Ӧ��ɳ��·������ʵ·���Ķ�Ӧ��ϵ�ɲμ���<br/>[Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ](../../../../file-management/app-sandbox-directory.md#Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ))��Ӧ����Ȩ�޷��ʵ�·����<br/><br/>image.PixelMap��ʾͼ�����ͼ������ռ�ô�С���ó���500KB��<br/>ͼ������ռ�ô�С���㹫ʽ��ͼ�����(����)��ͼ��߶� (����)��ÿ������ռ�õ��ֽ�����ͨ��Ϊ4�������磺һ�� 100x100 ��ͼƬ��ͼ<br/>������ռ�ô�СΪ100��100��4=40000�ֽڡ� |
| accountId | number | 是 | �û�ID��accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ��*@ohos.account.osAccount** to obtain the account ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId);
  console.info(`Succeeded in setting set watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}

```


## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties: WatermarkProperties): void
```

Ϊָ���û���ָ��Ӧ������ˮӡ���ԡ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ��� |
| bundleName | string | 是 | ������ˮӡ��Ӧ�ð����� |
| source | string \| image.PixelMap | 是 | ˮӡͼƬ����·�� |
| accountId | number | 是 | ϵͳ�˺�ID<br/><br/>ȡֵӦΪ��0�������� |
| properties | WatermarkProperties | 是 | ˮӡͼƬ������Ϣ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。示例代码水印属性行数和列数都设为1，会居中显示单个水印图片
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 1,
  intervalsCol: 1
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。设备屏幕宽高是1260*2720，水印图片宽高是100*100，示例代码水印属性行数为27，列数为12，按27行12列的网格布局排列显示27*12个水印图片
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 27,
  intervalsCol: 12
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。设备屏幕宽高是1260*2720，水印图片宽高是100*100，示例代码水印属性行数为28，列数为12，28 * 100 > 2720，网格布局无法适应窗口大小，水印会以窗口左上角为原点，以平铺方式重复覆盖整个应用窗口界面，超出界面右侧、下侧的水印图片会被裁剪
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 28,
  intervalsCol: 12
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}

```

