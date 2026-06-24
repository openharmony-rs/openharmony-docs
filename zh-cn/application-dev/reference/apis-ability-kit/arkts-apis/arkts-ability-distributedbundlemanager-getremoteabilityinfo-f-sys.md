# getRemoteAbilityInfo（系统接口）

## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void
```

��ȡ��elementNameָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ElementName��Ϣ�� |
| callback | AsyncCallback&lt;RemoteAbilityInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����óɹ�����errΪnull��dataΪ<br/>RemoteAbilityInfo���󣻵���ʧ��errΪ�������, dataΪundefined�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>
```

��ȡ��elementNameָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ElementName��Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteAbilityInfo&gt; | Promise���󣬵��óɹ�����RemoteAbilityInfo���󣻵���ʧ�ܷ��ش������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

��ȡ��elementNameָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo������Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ,������鳤��Ϊ10�� |
| callback | AsyncCallback&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����óɹ�����errΪnull<br/>��dataΪRemoteAbilityInfo������󣻵���ʧ��errΪ�������, dataΪundefined�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

��ȡ��elementNameָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo������Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ��������鳤��Ϊ10�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise���󣬵��óɹ�����RemoteAbilityInfo���󣻵���ʧ�ܷ��ش������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string, callback: AsyncCallback<RemoteAbilityInfo>): void
```

��ȡ��elementName��localeָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ElementName��Ϣ�� |
| locale | string | 是 | ���Ե����� |
| callback | AsyncCallback&lt;RemoteAbilityInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����óɹ�����errΪnull��dataΪ<br/>RemoteAbilityInfo���󣻵���ʧ��errΪ�������, dataΪundefined�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, locale: string): Promise<RemoteAbilityInfo>
```

��ȡ��elementName��localeָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ElementName��Ϣ�� |
| locale | string | 是 | ���Ե����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteAbilityInfo&gt; | Promise���󣬵��óɹ�����RemoteAbilityInfo���󣻵���ʧ�ܷ��ش������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string, callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

��ȡ��elementName��localeָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo������Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ,������鳤��Ϊ10�� |
| locale | string | 是 | ���Ե����� |
| callback | AsyncCallback&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����óɹ�����errΪnull<br/>��dataΪRemoteAbilityInfo������󣻵���ʧ��errΪ�������, dataΪundefined�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementNames: Array<ElementName>, locale: string): Promise<Array<RemoteAbilityInfo>>
```

��ȡ��elementName��localeָ����Զ���豸�ϵ�Ӧ�õ�AbilityInfo������Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ,������鳤��Ϊ10�� |
| locale | string | 是 | ���Ե����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise���󣬵��óɹ�����RemoteAbilityInfo���󣻵���ʧ�ܷ��ش������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability name is not found. |
| [17700007](../../errorcode-universal.md#17700007-The) | The specified device ID is not found. |
| [17700027](../../errorcode-universal.md#17700027-The) | The distributed service is not running. |

**示例：**

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

