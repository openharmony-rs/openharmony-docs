# off（系统接口）

## 导入模块

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## off('formAdd')

```TypeScript
function off(type: 'formAdd', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

取消订阅卡片新增事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formAdd' | 是 | 填写'formAdd'，表示卡片新增事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。 填写该参数时，与注册时填写bundleName的on接口对应。 缺省则取消订阅所有卡片使用方的卡片新增事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.RunningFormInfo&gt; | 否 | 回调函数。返回当前新增卡片信息。缺省时，表示注销对应已注册事件回调。 需与对应on('formAdd')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('formRemove')

```TypeScript
function off(type: 'formRemove', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

取消订阅卡片删除事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formRemove' | 是 | 填写'formRemove'，表示卡片删除事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。 填写该参数时，与注册时填写bundleName的on接口对应。 缺省则取消订阅所有卡片使用方的卡片删除事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.RunningFormInfo&gt; | 否 | 回调函数。返回当前删除卡片的信息。缺省时，表示注销对应已注册事件回调。 需与对应on('formRemove')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('notifyVisible')

```TypeScript
function off(
    type: 'notifyVisible',
    hostBundleName?: string,
    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>
  ): void
```

取消订阅通知卡片可见的事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyVisible' | 是 | 仅允许填写'notifyVisible'，表示取消订阅通知卡片为可见的事件。 |
| hostBundleName | string | 否 | 指定卡片使用方的bundleName，用于取消订阅卡片在该使用方的可见状态变更事件。 填写该参数时，与注册时填写bundleName的on接口对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | 否 | 回调函数。返回取消订阅该事件的卡片信息列表。缺省时，表示注销对应已注册订阅的回调。 需与对应on('notifyVisible')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('notifyInvisible')

```TypeScript
function off(
    type: 'notifyInvisible',
    hostBundleName?: string,
    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>
  ): void
```

取消订阅通知卡片不可见事件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyInvisible' | 是 | 仅允许填写'notifyInvisible'，表示卡片可见性变更为不可见。 |
| hostBundleName | string | 否 | 指定卡片使用方的bundleName，用于取消订阅卡片在该使用方的不可见状态变更事件。 填写该参数时，与注册时填写bundleName的on接口对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | 否 | 回调函数。返回取消订阅通知卡片不可见的卡片信息列表。缺省时，表示注销对应已注册事件 回调。需与对应on('notifyInvisible')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('router')

```TypeScript
function off(type: 'router', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

取消订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'router' | 是 | 填写'router'，表示取消订阅卡片的router事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。 填写该参数时，与注册时填写bundleName的on接口对应。 缺省则取消订阅所有卡片使用方点击router类型卡片的事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.RunningFormInfo&gt; | 否 | 回调函数。返回触发router事件的卡片信息。缺省时，表示注销对应bundleName下已注册事 件回调。 需与对应on('router')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('message')

```TypeScript
function off(type: 'message', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

取消订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片的信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 填写'message'，表示取消订阅卡片的message事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。 填写该参数时，与注册时填写bundleName的on接口对应。 缺省则取消订阅所有卡片使用方的message事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.RunningFormInfo&gt; | 否 | 回调函数。返回触发message事件的卡片的信息。缺省时，表示注销对应已注册事件回调。 需与对应on('message')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## off('call')

```TypeScript
function off(type: 'call', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

取消订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'call' | 是 | 填写'call'，表示取消订阅卡片的call事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。 填写该参数时，与注册时填写bundleName的on接口对应。 缺省则取消订阅所有卡片使用方的call事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;formInfo.RunningFormInfo&gt; | 否 | 回调函数。返回触发call事件的卡片信息。缺省时，表示注销对应已注册事件回调。 需与对应on('call')的callback一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
