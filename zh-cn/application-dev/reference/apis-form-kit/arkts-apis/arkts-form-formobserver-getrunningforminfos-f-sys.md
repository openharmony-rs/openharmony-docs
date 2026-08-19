# getRunningFormInfos（系统接口）

## 导入模块

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## getRunningFormInfos

```TypeScript
function getRunningFormInfos(callback: AsyncCallback<Array<formInfo.RunningFormInfo>>, hostBundleName?: string): void
```

获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function getRunningFormInfos(callback: AsyncCallback<Array<formInfo.RunningFormInfo>>, hostBundleName?: string): void--><!--Device-formObserver-function getRunningFormInfos(callback: AsyncCallback<Array<formInfo.RunningFormInfo>>, hostBundleName?: string): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | 是 | 回调函数。获取设备上正在运行的所有非临时卡片信息。当获取卡片信息成功时，error为 undefined，data为查询到的卡片信息。 |
| hostBundleName | string | 否 | 指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## getRunningFormInfos

```TypeScript
function getRunningFormInfos(
    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>,
    isUnusedIncluded: boolean,
    hostBundleName?: string
  ): void
```

获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function getRunningFormInfos(    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>,    isUnusedIncluded: boolean,    hostBundleName?: string  ): void--><!--Device-formObserver-function getRunningFormInfos(    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>,    isUnusedIncluded: boolean,    hostBundleName?: string  ): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | 是 | 回调函数。获取设备上正在运行的所有非临时卡片信息。当获取成功时，回调中的error为 undefined，data为查询到的卡片信息。 |
| isUnusedIncluded | boolean | 是 | 表示是否包含未使用的卡片。 <br>true: 表示包含未使用的卡片。 <br>false: 表示不包含未使用的卡片。 |
| hostBundleName | string | 否 | 指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## getRunningFormInfos

```TypeScript
function getRunningFormInfos(hostBundleName?: string): Promise<Array<formInfo.RunningFormInfo>>
```

获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function getRunningFormInfos(hostBundleName?: string): Promise<Array<formInfo.RunningFormInfo>>--><!--Device-formObserver-function getRunningFormInfos(hostBundleName?: string): Promise<Array<formInfo.RunningFormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 否 | 指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | Promise对象。返回设备上正在运行的所有非临时卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## getRunningFormInfos

```TypeScript
function getRunningFormInfos(
    isUnusedIncluded: boolean,
    hostBundleName?: string
  ): Promise<Array<formInfo.RunningFormInfo>>
```

获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function getRunningFormInfos(    isUnusedIncluded: boolean,    hostBundleName?: string  ): Promise<Array<formInfo.RunningFormInfo>>--><!--Device-formObserver-function getRunningFormInfos(    isUnusedIncluded: boolean,    hostBundleName?: string  ): Promise<Array<formInfo.RunningFormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isUnusedIncluded | boolean | 是 | 表示是否包含未使用的卡片。 <br>true: 表示包含未使用的卡片。 <br>false: 表示不包含未使用的卡片。 |
| hostBundleName | string | 否 | 指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | Promise对象。返回设备上正在运行的所有非临时卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

