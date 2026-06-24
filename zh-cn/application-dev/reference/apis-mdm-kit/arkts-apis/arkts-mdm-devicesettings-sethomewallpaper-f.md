# setHomeWallpaper

## setHomeWallpaper

```TypeScript
function setHomeWallpaper(admin: Want, fd: number):  Promise<void>
```

���������ֽ��ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_WALLPAPER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| fd | number | 是 | ��Ҫ����Ϊ�����ֽͼƬ���ļ�������������ͨ��file.fs��<br/>[openSync](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopensync)�ӿڻ�ȡӦ��ɳ��Ŀ¼�µ�ͼƬ�ļ�����������ֽͼƬ��С��<br/>�ܳ���100MB�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵����������ֽʧ�ܺ���׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs }  from '@kit.CoreFileKit';

let wantTemp: Want = {
  // 请根据实际情况修改
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 参数根据实际情况进行替换
let filename: string = "homewallpaper.jpg";
let filePath: string = context.filesDir + '/' + filename;
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_WRITE).fd;
deviceSettings.setHomeWallpaper(wantTemp, fd).then(() => {
  console.info('Succeeded in setting home wallpaper');
}).catch((err: BusinessError) => {
  console.error(`Failed to set home wallpaper. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  fs.closeSync(fd);
});

```

