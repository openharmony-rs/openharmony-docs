# getRemoteAbilityInfo（系统接口）

## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void
```

获取由elementName指定的远程设备上的应用的AbilityInfo信息。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElementName信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RemoteAbilityInfo&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，调用成功返回err为null，data为RemoteAbilityInfo对象；调用失败err为错误对象, data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo) => {
            if (err) {
                console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
            } else {
                console.info('Operation succeed:' + JSON.stringify(data));
            }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, (err: BusinessError | null, data: distributedBundleManager.RemoteAbilityInfo | undefined) => {
            if (err) {
                console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
            } else {
                console.info('Operation succeed:' + JSON.stringify(data));
            }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>
```

获取由elementName指定的远程设备上的应用的AbilityInfo信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElementName信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteAbilityInfo&gt; | Promise对象，调用成功返回RemoteAbilityInfo对象；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }).then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }).then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: Error) => {
            console.error(`Operation failed: error code is ${(err as BusinessError).code}  and error message is ${(err as BusinessError).message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

获取由elementName指定的远程设备上的应用的AbilityInfo数组信息。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息,最大数组长度为10。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，调用成功返回err为null，data为RemoteAbilityInfo数组对象；调用失败err为错误对象, data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application1',
                abilityName: 'EntryAbility1'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo[]) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
let elementNames: Array<bundleManager.ElementName> = [
    {
        deviceId: '1',
        bundleName: 'com.example.application1',
        abilityName: 'EntryAbility1'
    },
    {
        deviceId: '1',
        bundleName: 'com.example.application2',
        abilityName: 'EntryAbility'
    }
]
try {
    distributedBundleManager.getRemoteAbilityInfo(
        elementNames, (err: BusinessError | null, data: distributedBundleManager.RemoteAbilityInfo[] | undefined) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

获取由elementName指定的远程设备上的应用的AbilityInfo数组信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息，最大数组长度为10。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise对象，调用成功返回RemoteAbilityInfo对象；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application',
                abilityName: 'EntryAbility'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ]).then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
let elementNames: Array<bundleManager.ElementName> = [
    {
        deviceId: '1',
        bundleName: 'com.example.application1',
        abilityName: 'EntryAbility1'
    },
    {
        deviceId: '1',
        bundleName: 'com.example.application2',
        abilityName: 'EntryAbility'
    }
]
try {
    distributedBundleManager.getRemoteAbilityInfo(elementNames).then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: Error) => {
            console.error(`Operation failed: error code is ${(err as BusinessError).code}  and error message is ${(err as BusinessError).message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string, callback: AsyncCallback<RemoteAbilityInfo>): void
```

获取由elementName和locale指定的远程设备上的应用的AbilityInfo信息。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, locale: string, callback: AsyncCallback<RemoteAbilityInfo>): void--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, locale: string, callback: AsyncCallback<RemoteAbilityInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElementName信息。 |
| locale | string | 是 | 语言地区。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RemoteAbilityInfo&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，调用成功返回err为null，data为RemoteAbilityInfo对象；调用失败err为错误对象, data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN', (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN', (err: BusinessError | null, data: distributedBundleManager.RemoteAbilityInfo | undefined) => {
          if (err) {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string): Promise<RemoteAbilityInfo>
```

获取由elementName和locale指定的远程设备上的应用的AbilityInfo信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, locale: string): Promise<RemoteAbilityInfo>--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementName: ElementName, locale: string): Promise<RemoteAbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElementName信息。 |
| locale | string | 是 | 语言地区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteAbilityInfo&gt; | Promise对象，调用成功返回RemoteAbilityInfo对象；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
try {
    distributedBundleManager.getRemoteAbilityInfo(
        {
            deviceId: '1',
            bundleName: 'com.example.application',
            abilityName: 'EntryAbility'
        }, 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: Error) => {
            console.error(`Operation failed: error code is ${(err as BusinessError).code}  and error message is ${(err as BusinessError).message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

获取由elementName和locale指定的远程设备上的应用的AbilityInfo数组信息。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息,最大数组长度为10。 |
| locale | string | 是 | 语言地区。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，调用成功返回err为null，data为RemoteAbilityInfo数组对象；调用失败err为错误对象, data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application1',
                abilityName: 'EntryAbility1'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], 'zh-Hans-CN', (err: BusinessError, data: distributedBundleManager.RemoteAbilityInfo[]) => {
          if (err) {
           console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
let elementNames: Array<bundleManager.ElementName> = [
    {
        deviceId: '1',
        bundleName: 'com.example.application1',
        abilityName: 'EntryAbility1'
    },
    {
        deviceId: '1',
        bundleName: 'com.example.application2',
        abilityName: 'EntryAbility'
    }
]
try {
    distributedBundleManager.getRemoteAbilityInfo(
        elementNames, 'zh-Hans-CN', (err: BusinessError | null, data: distributedBundleManager.RemoteAbilityInfo[] | undefined) => {
          if (err) {
           console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
          } else {
            console.info('Operation succeed:' + JSON.stringify(data));
          }
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string): Promise<Array<RemoteAbilityInfo>>
```

获取由elementName和locale指定的远程设备上的应用的AbilityInfo数组信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string): Promise<Array<RemoteAbilityInfo>>--><!--Device-distributedBundleManager-function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string): Promise<Array<RemoteAbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息,最大数组长度为10。 |
| locale | string | 是 | 语言地区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise对象，调用成功返回RemoteAbilityInfo对象；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability name is not found. |
| [17700007](../errorcode-bundle.md#17700007-输入的设备id有误) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-分布式服务未启动) | The distributed service is not running. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedBundleManager.getRemoteAbilityInfo(
        [
            {
                deviceId: '1',
                bundleName: 'com.example.application',
                abilityName: 'EntryAbility'
            },
            {
                deviceId: '1',
                bundleName: 'com.example.application2',
                abilityName: 'EntryAbility'
            }
        ], 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
            console.error(`Operation failed: error code is ${err.code}  and error message is ${err.message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';

// 开发者需根据实际工程更新deviceId、bundleName和abilityName。
let elementNames: Array<bundleManager.ElementName> = [
    {
        deviceId: '1',
        bundleName: 'com.example.application1',
        abilityName: 'EntryAbility1'
    },
    {
        deviceId: '1',
        bundleName: 'com.example.application2',
        abilityName: 'EntryAbility'
    }
]
try {
    distributedBundleManager.getRemoteAbilityInfo(
        elementNames, 'zh-Hans-CN').then((data: distributedBundleManager.RemoteAbilityInfo[]) => {
            console.info('Operation succeed:' + JSON.stringify(data));
        }).catch((err: Error) => {
            console.error(`Operation failed: error code is ${(err as BusinessError).code}  and error message is ${(err as BusinessError).message}`);
        });
} catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Operation failed: error code is ${code}  and error message is ${message}`);
}
```

