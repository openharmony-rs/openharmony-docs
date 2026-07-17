# getTargetOverlayModuleInfos

## 导入模块

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## getTargetOverlayModuleInfos

```TypeScript
function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用callback异步回调。

**起始版本：** 10

<!--Device-overlay-function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void--><!--Device-overlay-function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetModuleName | string | 是 | 指定当前应用中的目标module的名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<OverlayModuleInfo>> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取指定的目标module的[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)成功时，err返回undefined。否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-指定的module是overlay特征的module) | The specified module is an overlay module. |

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

获取指定的目标module所关联的OverlayModuleInfo。overlay特征的module一般是为设备上存在的非overlay特征的module提供覆盖的资源文件，其中非overlay特征的module被称作目标module。使用Promise异步回调。

**起始版本：** 10

<!--Device-overlay-function getTargetOverlayModuleInfos(targetModuleName: string): Promise<Array<OverlayModuleInfo>>--><!--Device-overlay-function getTargetOverlayModuleInfos(targetModuleName: string): Promise<Array<OverlayModuleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetModuleName | string | 是 | 指定当前应用中的目标module的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<OverlayModuleInfo>> | Promise对象，返回&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md)&gt;&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-指定的module是overlay特征的module) | The specified module is an overlay module. |

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

