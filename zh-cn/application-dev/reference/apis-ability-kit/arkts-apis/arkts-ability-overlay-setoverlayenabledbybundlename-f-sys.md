# setOverlayEnabledByBundleName（系统接口）

## setOverlayEnabledByBundleName

```TypeScript
function setOverlayEnabledByBundleName(bundleName:string, moduleName:string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

����ָ��Ӧ�õ�overlay module�Ľ���ʹ��״̬��ʹ��callback�첽�ص���

ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.CHANGE_OVERLAY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundle���ơ� |
| moduleName | string | 是 | ָ��Ӧ�õ�overlay����module�����ơ� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |
| callback | AsyncCallback&lt;void&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������ָ��Ӧ�õ�overlay module�Ľ���ʹ��״̬�ɹ�ʱ��<br/>errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700032](../../errorcode-universal.md#17700032-The) | The specified bundle does not contain any overlay module. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";
let isEnabled = false;

try {
  overlay.setOverlayEnabledByBundleName(bundleName, moduleName, isEnabled, (err, data) => {
    if (err) {
      console.error('setOverlayEnabledByBundleName failed due to err code: ' + err.code + ' ' + 'message:' +
      err.message);
      return;
    }
    console.info('setOverlayEnabledByBundleName successfully');
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabledByBundleName failed due to err code: ' + code + ' ' + 'message:' + message);
}

```


## setOverlayEnabledByBundleName

```TypeScript
function setOverlayEnabledByBundleName(bundleName:string, moduleName:string, isEnabled: boolean): Promise<void>
```

����ָ��Ӧ�õ�overlay module�Ľ���ʹ��״̬��ʹ��Promise�첽�ص���

ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.CHANGE_OVERLAY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundle���ơ� |
| moduleName | string | 是 | ָ��Ӧ�õ�overlay module�����ơ� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module name is not found. |
| [17700032](../../errorcode-universal.md#17700032-The) | The specified bundle does not contain any overlay module. |
| [17700033](../../errorcode-universal.md#17700033-The) | The specified module is not an overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";
let isEnabled = false;

try {

  overlay.setOverlayEnabledByBundleName(bundleName, moduleName, isEnabled)
    .then((data) => {
      console.info('setOverlayEnabledByBundleName successfully');
    }).catch((err: BusinessError) => {
    console.error('setOverlayEnabledByBundleName failed due to err code: ' + err.code + ' ' + 'message:' + err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabledByBundleName failed due to err code: ' + code + ' ' + 'message:' + message);
}

```

