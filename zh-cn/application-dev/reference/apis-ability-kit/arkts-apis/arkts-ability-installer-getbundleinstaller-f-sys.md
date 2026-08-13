# getBundleInstaller（系统接口）

## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

获取BundleInstaller对象。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-installer-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void--><!--Device-installer-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;BundleInstaller&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，获取BundleInstaller对象，err 为undefined，data为获取到的BundleInstaller对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    installer.getBundleInstaller((err: BusinessError, data: installer.BundleInstaller) => {
        if (err) {
            console.error('getBundleInstaller failed:' + err.message);
        } else {
            console.info('getBundleInstaller successfully');
        }
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed:' + message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    installer.getBundleInstaller((err: BusinessError | null, data: installer.BundleInstaller | undefined) => {
        if (err) {
            console.error('getBundleInstaller failed:' + err.message);
        } else {
            console.info('getBundleInstaller successfully');
        }
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed:' + message);
}
```


## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

获取BundleInstaller对象。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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

## 示例

ArkTS-Dyn示例:

```TypeScript
import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        console.info('getBundleInstaller successfully.');
    }).catch((error: BusinessError) => {
        console.error('getBundleInstaller failed. Cause: ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { installer } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    installer.getBundleInstaller().then((data: installer.BundleInstaller) => {
        console.info('getBundleInstaller successfully.');
    }).catch((error: Error) => {
        console.error('getBundleInstaller failed. Cause: ' + (error as BusinessError).message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('getBundleInstaller failed. Cause: ' + message);
}
```

