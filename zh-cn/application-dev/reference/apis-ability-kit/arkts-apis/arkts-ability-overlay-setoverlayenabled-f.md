# setOverlayEnabled

## setOverlayEnabled

```TypeScript
function setOverlayEnabled(moduleName:string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

���õ�ǰӦ����overlay module�Ľ���ʹ��״̬��ʹ��callback�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | overlay����module�����ơ� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������ָ��module��overlay����ʹ��״̬�ɹ�ʱ��errΪ<br/>undefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";
let isEnabled = false;

try {
  overlay.setOverlayEnabled(moduleName, isEnabled, (err, data) => {
    if (err) {
      console.error('setOverlayEnabled failed due to err code: ' + err.code + ' ' + 'message:' + err.message);
      return;
    }
    console.info('setOverlayEnabled success');
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabled failed due to err code: ' + code + ' ' + 'message:' + message);
}

```


## setOverlayEnabled

```TypeScript
function setOverlayEnabled(moduleName:string, isEnabled: boolean): Promise<void>
```

���õ�ǰӦ����overlay����module�Ľ���ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | overlay����module�����ơ� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";
let isEnabled = false;

try {
  overlay.setOverlayEnabled(moduleName, isEnabled)
    .then(() => {
      console.info('setOverlayEnabled success');
    }).catch((err: BusinessError) => {
    console.error('setOverlayEnabled failed due to err code: ' + err.code + ' ' + 'message:' + err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabled failed due to err code: ' + code + ' ' + 'message:' + message);
}

```

