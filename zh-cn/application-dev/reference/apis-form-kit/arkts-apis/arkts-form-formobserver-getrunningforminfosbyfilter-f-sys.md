# getRunningFormInfosByFilter（系统接口）

## 导入模块

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## getRunningFormInfosByFilter

```TypeScript
function getRunningFormInfosByFilter(
    formProviderFilter: formInfo.FormProviderFilter
  ): Promise<Array<formInfo.RunningFormInfo>>
```

根据提供方信息查询已添加的卡片信息列表。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formObserver-function getRunningFormInfosByFilter(    formProviderFilter: formInfo.FormProviderFilter  ): Promise<Array<formInfo.RunningFormInfo>>--><!--Device-formObserver-function getRunningFormInfosByFilter(    formProviderFilter: formInfo.FormProviderFilter  ): Promise<Array<formInfo.RunningFormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formProviderFilter | formInfo.FormProviderFilter | 是 | 卡片提供方应用信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | Promise对象。返回已添加的卡片信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |


## getRunningFormInfosByFilter

```TypeScript
function getRunningFormInfosByFilter(
    formProviderFilter: formInfo.FormProviderFilter,
    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>
  ): void
```

根据提供方信息查询已添加的卡片信息列表。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formObserver-function getRunningFormInfosByFilter(    formProviderFilter: formInfo.FormProviderFilter,    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>  ): void--><!--Device-formObserver-function getRunningFormInfosByFilter(    formProviderFilter: formInfo.FormProviderFilter,    callback: AsyncCallback<Array<formInfo.RunningFormInfo>>  ): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formProviderFilter | formInfo.FormProviderFilter | 是 | 卡片提供方应用信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | 是 | 回调函数。返回已添加的卡片信息列表。error为undefined，data为查询到的卡片信 息列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

