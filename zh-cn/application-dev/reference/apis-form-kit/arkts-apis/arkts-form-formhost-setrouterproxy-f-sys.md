# setRouterProxy（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>, callback: AsyncCallback<void>): void
```

设置卡片跳转代理。使用callback异步回调，返回卡片跳转所需要Want信息。 > **说明：** > > - 一般情况下，对于桌面添加的卡片，当卡片触发router跳转时，卡片框架会检测其跳转目的地是否合理，是否有跳转权限，然后进行应用跳转。如果卡片使用方添加了卡片，并设置了卡片跳转代理，那么卡片触发router跳转时，卡片框架不 > 会再为其进行跳转操作，会把包含跳转目的地的want参数返回给卡片使用方。因此如果卡片使用方希望使用该want信息进行应用跳转，需要确保自身拥有应用跳转的权限，参考 > [UIAbilityContext.startAbility()](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability) > 接口。 > > - 一个formId最多只能设置一个跳转代理，多次设置后，最后设置的proxy生效。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>, callback: AsyncCallback<void>): void--><!--Device-formHost-function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识数组。 |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。返回跳转所需要的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当指定卡片设置router跳转代理成功时，error为undefined；否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>): Promise<void>
```

设置卡片跳转代理。使用Promise异步回调，返回卡片跳转所需要Want信息。 > **说明：** > > - 一般情况下，对于桌面添加的卡片，当卡片触发router跳转时，卡片框架会检测其跳转目的地是否合理，是否有跳转权限，然后进行应用跳转。如果卡片使用方添加了卡片，并设置了卡片跳转代理，那么卡片触发router跳转时，卡片框架不 > 会再为其进行跳转操作，会把包含跳转目的地的want参数返回给卡片使用方。因此如果卡片使用方希望使用该want信息进行应用跳转，需要确保自身拥有应用跳转的权限，参考 > [UIAbilityContext.startAbility()](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability) > 接口。 > > - 一个formId最多只能设置一个跳转代理，多次设置后，最后设置的proxy生效。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>): Promise<void>--><!--Device-formHost-function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识数组。 |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。返回跳转所需要的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

