# off（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## off("formUninstall")

```TypeScript
function off(type: "formUninstall", callback?: Callback<string>): void
```

取消订阅卡片卸载事件。使用callback异步回调。

> **说明：**
> 
> 卡片卸载与卡片移除不同。当应用卸载时，对应的卡片会自动卸载。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | "formUninstall" | 是 | 填写'formUninstall'，表示卡片卸载事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 回调函数，返回卡片标识。缺省时，表示注销所有已注册事件回调。 需与对应on('formUninstall')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('formOverflow')

```TypeScript
function off(type: 'formOverflow', callback?: Callback<formInfo.OverflowRequest>): void
```

取消订阅互动卡片动效请求事件。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formOverflow' | 是 | 事件回调类型，支持的事件为'formOverflow'，表示互动卡片动效请求。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.OverflowRequest&gt; | 否 | 回调函数，对应已订阅互动卡片动效请求。缺省时，表示注销所有已注册互动卡片动效请求事件回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('formOverflow', (request: formInfo.OverflowRequest) => {
    console.info(`formHost off formOverflow, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## off('changeSceneAnimationState')

```TypeScript
function off(type: 'changeSceneAnimationState', 
    callback?: Callback<formInfo.ChangeSceneAnimationStateRequest>): void
```

取消订阅互动卡片状态切换请求事件。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。使用 callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'changeSceneAnimationState' | 是 | 事件回调类型，支持的事件为'changeSceneAnimationState'，表示互动卡片状态切换。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.ChangeSceneAnimationStateRequest&gt; | 否 | 回调函数，对应已订阅互动卡片状态切换请求。缺省时，表示注销所有已注册互动卡片状 态切换事件回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('changeSceneAnimationState', (request: formInfo.ChangeSceneAnimationStateRequest): void => {
    console.info(`formHost off changeSceneAnimationState, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## off('getFormRect')

```TypeScript
function off(type: 'getFormRect', callback?: formInfo.GetFormRectInfoCallback): void
```

取消订阅卡片位置尺寸查询请求事件。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getFormRect' | 是 | 事件回调类型，支持的事件为'getFormRect'，表示卡片位置尺寸查询。 |
| callback | formInfo.GetFormRectInfoCallback | 否 | 回调函数，对应已订阅卡片位置尺寸查询请求。缺省时，表示注销所有已注册卡片位置、尺寸查询事件回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('getFormRect');
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## off('getLiveFormStatus')

```TypeScript
function off(type: 'getLiveFormStatus', 
    callback?: formInfo.GetLiveFormStatusCallback): void
```

Cancels Listening to the event of get live form status.

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getLiveFormStatus' | 是 | Indicates event type. |
| callback | formInfo.GetLiveFormStatusCallback | 否 | The callback of get live form status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
