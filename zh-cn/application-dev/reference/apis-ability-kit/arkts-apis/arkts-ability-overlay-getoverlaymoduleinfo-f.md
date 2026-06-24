# getOverlayModuleInfo

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void
```

��ȡ��ǰӦ����overlay����module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ָ����ǰӦ���е�overlay����module�����ơ� |
| callback | AsyncCallback&lt;OverlayModuleInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ��ǰӦ����ָ����module��<br/>[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)��Ϣ�ɹ�ʱ��err����undefined������ص��������ؾ������<br/>���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700032](../../errorcode-universal.md#17700032-The) | The specified bundle does not contain any overlay module. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";

try {
  overlay.getOverlayModuleInfo(moduleName, (err, data) => {
    if (err) {
      console.error('getOverlayModuleInfo failed due to err code : ' + err.code + ' ' + 'message :' + err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getOverlayModuleInfo failed due to err code : ' + code + ' ' + 'message :' + message);
}

```


## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string): Promise<OverlayModuleInfo>
```

��ȡ��ǰӦ����overlay����module��OverlayModuleInfo��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ָ����ǰӦ���е�overlay module�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OverlayModuleInfo&gt; | Promise���󣬷���<br/>[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700032](../../errorcode-universal.md#17700032-The) | The specified bundle does not contain any overlay module. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";

(async () => {
  try {
    let overlayModuleInfo = await overlay.getOverlayModuleInfo(moduleName);
    console.info('overlayModuleInfo is ' + JSON.stringify(overlayModuleInfo));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getOverlayModuleInfo failed due to err code : ' + code + ' ' + 'message :' + message);
  }
})();

```

