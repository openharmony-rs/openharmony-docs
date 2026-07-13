# getOverlayModuleInfo

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void
```

获取当前应用中overlay特征module的OverlayModuleInfo信息。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 指定当前应用中的overlay特征module的名称。 |
| callback | AsyncCallback&lt;OverlayModuleInfo&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，当获取当前应用中指定的module的[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)信息成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700032](../errorcode-bundle.md#17700032-指定的应用不包含overlay特征的module) | The specified bundle does not contain any overlay module. |
| [17700033](../errorcode-bundle.md#17700033-指定的module不是overlay特征的module) | The specified module is not an overlay module. |

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

获取当前应用中overlay特征module的OverlayModuleInfo信息。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 指定当前应用中的overlay module的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OverlayModuleInfo&gt; | Promise对象，返回[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700032](../errorcode-bundle.md#17700032-指定的应用不包含overlay特征的module) | The specified bundle does not contain any overlay module. |
| [17700033](../errorcode-bundle.md#17700033-指定的module不是overlay特征的module) | The specified module is not an overlay module. |

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

