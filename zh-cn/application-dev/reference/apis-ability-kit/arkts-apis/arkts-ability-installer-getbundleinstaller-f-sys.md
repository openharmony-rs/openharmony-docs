# getBundleInstaller（系统接口）

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

获取BundleInstaller对象。使用callback异步回调。

**起始版本：** 9

<!--Device-installer-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void--><!--Device-installer-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;BundleInstaller&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，获取BundleInstaller对象，err为undefined，data为获取到的BundleInstaller对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |


## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

获取BundleInstaller对象。使用Promise异步回调。

**起始版本：** 9

<!--Device-installer-function getBundleInstaller(): Promise<BundleInstaller>--><!--Device-installer-function getBundleInstaller(): Promise<BundleInstaller>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInstaller&gt; | BundleInstaller object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

