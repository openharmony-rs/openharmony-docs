# getOverlayModuleInfoByBundleName（系统接口）

## getOverlayModuleInfoByBundleName

```TypeScript
function getOverlayModuleInfoByBundleName(bundleName: string,
      callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

��ȡָ��Ӧ��������module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���

ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundle���ơ� |
| callback | AsyncCallback&lt;Array&lt;OverlayModuleInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡָ��Ӧ��������<br/>module��[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)��Ϣ�ɹ�ʱ��err����undefined������ص���<br/>�����ؾ��������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700032](../../errorcode-universal.md#17700032-The) | The specified bundle does not contain any overlay module. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "com.example.myapplication_xxxxx";

try {
  overlay.getOverlayModuleInfoByBundleName(bundleName, (err, data) => {
    if (err) {
      console.error('getOverlayModuleInfoByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getOverlayModuleInfoByBundleName failed due to err code : ' + code + ' ' + 'message :' + message);
}

```


## getOverlayModuleInfoByBundleName

```TypeScript
function getOverlayModuleInfoByBundleName(bundleName: string, moduleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

��ȡָ��Ӧ����ָ��module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���

ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundle���ơ� |
| moduleName | string | 是 | ָ��Ӧ���е�overlay module�����ơ�ȱʡ���ֶ�ʱ����ѯ�ӿڽ���ѯָ��Ӧ��������module��OverlayModuleInfo��Ϣ�� |
| callback | AsyncCallback&lt;Array&lt;OverlayModuleInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡָ��Ӧ����ָ��<br/>module��[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)��Ϣ�ɹ�ʱ��err����undefined������ص���<br/>�����ؾ��������� |

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

try {
  overlay.getOverlayModuleInfoByBundleName(bundleName, moduleName, (err, data) => {
    if (err) {
      console.error('getOverlayModuleInfoByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getOverlayModuleInfoByBundleName failed due to err code : ' + code + ' ' + 'message :' + message);
}

```


## getOverlayModuleInfoByBundleName

```TypeScript
function getOverlayModuleInfoByBundleName(bundleName: string, moduleName?: string): Promise<Array<OverlayModuleInfo>>
```

��ȡָ��Ӧ����ָ��module��OverlayModuleInfo��Ϣ��ʹ��promise�첽�ص���

ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundle���ơ� |
| moduleName | string | 否 | ָ��Ӧ���е�overlay module�����ơ�Ĭ��ֵ��ȱʡ���ֶ�ʱ����ѯ�ӿڽ���ѯָ��Ӧ��������module��OverlayModuleInfo��Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OverlayModuleInfo&gt;&gt; | Promise���󣬷���&gt;�� |

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

(async () => {
  try {
    let overlayModuleInfos = await overlay.getOverlayModuleInfoByBundleName(bundleName, moduleName);
    console.info('overlayModuleInfos are ' + JSON.stringify(overlayModuleInfos));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getTargetOverlayModuleInfos failed due to err code : ' + code + ' ' + 'message :' + message);
  }
})();

```

