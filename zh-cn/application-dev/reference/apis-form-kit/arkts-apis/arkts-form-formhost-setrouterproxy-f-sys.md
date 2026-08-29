# setRouterProxy（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>, callback: AsyncCallback<void>): void
```

设置卡片跳转代理。使用callback异步回调，返回卡片跳转所需要Want信息。

> **说明：**
> 
> - 一般情况下，对于桌面添加的卡片，当卡片触发router跳转时，卡片框架会检测其跳转目的地是否合理，是否有跳转权限，然后进行应用跳转。如果卡片使用方添加了卡片，并设置了卡片跳转代理，那么卡片触发router跳转时，卡片框架不
> 会再为其进行跳转操作，会把包含跳转目的地的want参数返回给卡片使用方。因此如果卡片使用方希望使用该want信息进行应用跳转，需要确保自身拥有应用跳转的权限，参考
> [UIAbilityContext.startAbility()](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability)
> 接口。
> 
> - 一个formId最多只能设置一个跳转代理，多次设置后，最后设置的proxy生效。

**起始版本：** 11

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array &lt;string&gt; | 是 | 卡片标识数组。 |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。返回跳转所需要的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当指定卡片设置router跳转代理成功时，error为undefined；否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |

**示例**

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CardExample {
  @State formId: number = 0;
  @State fwidth: number = 420;
  @State fheight: number = 280;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      FormComponent({
        id: this.formId,
        name: "widget",
        bundle: "com.example.cardprovider",
        ability: "EntryFormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false,
      })
        .allowUpdate(true)
        .size({ width: this.fwidth, height: this.fheight })
        .visibility(Visibility.Visible)
        .onAcquired((form) => {
          console.info('testTag onAcquired.');
          this.formId = form.id;
          try {
            let formIds: string[] = [this.formId.toString()];
            formHost.setRouterProxy(formIds, (want: Want) => {
              console.info('formHost recv router event.');
              // 卡片使用方自己处理跳转
              this.context.startAbility(want, (err: BusinessError) => {
                console.error(`formHost startAbility error, code: ${err.code}, message: ${err.message}`);
              });
            }, (err: BusinessError) => {
              console.error(`set router proxy error, code: ${err.code}, message: ${err.message}`);
            })
          } catch (e) {
            console.error(`formHost setRouterProxy, code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```


## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>): Promise<void>
```

设置卡片跳转代理。使用Promise异步回调，返回卡片跳转所需要Want信息。

> **说明：**
> 
> - 一般情况下，对于桌面添加的卡片，当卡片触发router跳转时，卡片框架会检测其跳转目的地是否合理，是否有跳转权限，然后进行应用跳转。如果卡片使用方添加了卡片，并设置了卡片跳转代理，那么卡片触发router跳转时，卡片框架不
> 会再为其进行跳转操作，会把包含跳转目的地的want参数返回给卡片使用方。因此如果卡片使用方希望使用该want信息进行应用跳转，需要确保自身拥有应用跳转的权限，参考
> [UIAbilityContext.startAbility()](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability)
> 接口。
> 
> - 一个formId最多只能设置一个跳转代理，多次设置后，最后设置的proxy生效。

**起始版本：** 11

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array &lt;string&gt; | 是 | 卡片标识数组。 |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。返回跳转所需要的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |

**示例**

```TypeScript
import { formHost } from '@kit.FormKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CardExample {
  @State formId: number = 0;
  @State fwidth: number = 420;
  @State fheight: number = 280;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      FormComponent({
        id: this.formId,
        name: "widget",
        bundle: "com.example.cardprovider",
        ability: "EntryFormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false,
      })
        .allowUpdate(true)
        .size({ width: this.fwidth, height: this.fheight })
        .visibility(Visibility.Visible)
        .onAcquired((form) => {
          console.info('testTag onAcquired.');
          this.formId = form.id;
          try {
            let formIds: string[] = [this.formId.toString()];
            formHost.setRouterProxy(formIds, (want: Want) => {
              console.info('formHost recv router event.');
              // 卡片使用方自己处理跳转
              this.context.startAbility(want, (err: BusinessError) => {
                console.error(`formHost startAbility error, code: ${err.code}, message: ${err.message}`);
              });
            }).then(() => {
              console.info('formHost set router proxy success');
            }).catch((err: BusinessError) => {
              console.error(`set router proxy error, code: ${err.code}, message: ${err.message}`);
            })
          } catch (e) {
            console.error(`formHost setRouterProxy, code: ${e.code}, message: ${e.message}`);
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
