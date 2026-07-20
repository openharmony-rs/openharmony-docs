# getTargetOverlayModuleInfosByBundleName（系统接口）

## 导入模块

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

<a id="gettargetoverlaymoduleinfosbybundlename"></a>
## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string,
      callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

获取指定应用中所有module关联的所有OverlayModuleInfo信息。使用callback异步回调。

指定应用是调用方自身时不需要权限。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string,
      callback: AsyncCallback<Array<OverlayModuleInfo>>): void--><!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string,
      callback: AsyncCallback<Array<OverlayModuleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetBundleName | string | 是 | 指定目标应用的bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;OverlayModuleInfo&gt;&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取指定应用中所有module关联的所有[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)信息成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700035](../errorcode-bundle.md#17700035-指定的应用只包含overlay特征的module) | The specified bundle is an overlay bundle. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";

try {
  overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
    message);
}

```


<a id="gettargetoverlaymoduleinfosbybundlename-1"></a>
## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用callback异步回调。

指定应用是调用方自身时不需要权限。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void--><!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetBundleName | string | 是 | 指定目标应用的bundle名称。 |
| moduleName | string | 是 | 指定应用中的目标module的名称。缺省该字段时，查询接口将查询指定应用中所有module所关联的OverlayModuleInfo信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;OverlayModuleInfo&gt;&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取指定应用中指定module关联的所有[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)信息成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-指定的module是overlay特征的module) | The specified module is an overlay module. |
| [17700035](../errorcode-bundle.md#17700035-指定的应用只包含overlay特征的module) | The specified bundle is an overlay bundle. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";

try {
  overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, moduleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
    message);
}

```


<a id="gettargetoverlaymoduleinfosbybundlename-2"></a>
## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName?: string): Promise<Array<OverlayModuleInfo>>
```

获取指定应用中指定module关联的所有OverlayModuleInfo信息。使用promise异步回调。

指定应用是调用方自身时不需要权限。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName?: string): Promise<Array<OverlayModuleInfo>>--><!--Device-overlay-function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName?: string): Promise<Array<OverlayModuleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetBundleName | string | 是 | 指定目标应用的bundle名称。 |
| moduleName | string | 否 | 指定应用中的目标module的名称。默认值：缺省该字段时，查询接口将查询指定应用中所有module所关联的OverlayModuleInfo信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OverlayModuleInfo&gt;&gt; | Promise对象，返回<Array<[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)>>。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-指定的module是overlay特征的module) | The specified module is an overlay module. |
| [17700035](../errorcode-bundle.md#17700035-指定的应用只包含overlay特征的module) | The specified bundle is an overlay bundle. |

**示例：**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";

(async () => {
  try {
    let overlayModuleInfos = await overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, moduleName);
    console.info('overlayModuleInfos are ' + JSON.stringify(overlayModuleInfos));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
      message);
  }
})();

```

