# getTargetOverlayModuleInfos

## getTargetOverlayModuleInfos

```TypeScript
function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

��ȡָ����Ŀ��module��������OverlayModuleInfo��overlay������moduleһ����Ϊ�豸�ϴ��ڵķ�overlay������module�ṩ���ǵ���Դ�ļ������з�overlay������module������Ŀ��
module��ʹ��callback�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetModuleName | string | 是 | ָ����ǰӦ���е�Ŀ��module�����ơ� |
| callback | AsyncCallback&lt;Array&lt;OverlayModuleInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡָ����Ŀ��module<br/>��[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)�ɹ�ʱ��err����undefined������ص��������ؾ�������<br/>�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700034](../../errorcode-universal.md#17700034-The) | The specified module is an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetModuleName = "feature";

try {
  overlay.getTargetOverlayModuleInfos(targetModuleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfos failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfos failed due to err code : ' + code + ' ' + 'message :' + message);
}

```


## getTargetOverlayModuleInfos

```TypeScript
function getTargetOverlayModuleInfos(targetModuleName: string): Promise<Array<OverlayModuleInfo>>
```

��ȡָ����Ŀ��module��������OverlayModuleInfo��overlay������moduleһ����Ϊ�豸�ϴ��ڵķ�overlay������module�ṩ���ǵ���Դ�ļ������з�overlay������module������Ŀ��
module��ʹ��Promise�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetModuleName | string | 是 | ָ����ǰӦ���е�Ŀ��module�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OverlayModuleInfo&gt;&gt; | Promise���󣬷���&gt;�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700034](../../errorcode-universal.md#17700034-The) | The specified module is an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetModuleName = "feature";

(async () => {
  try {
    let overlayModuleInfos = await overlay.getTargetOverlayModuleInfos(targetModuleName);
    console.info('overlayModuleInfos are ' + JSON.stringify(overlayModuleInfos));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getTargetOverlayModuleInfos failed due to err code : ' + code + ' ' + 'message :' + message);
  }
})();

```

