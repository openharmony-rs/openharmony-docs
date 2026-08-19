# ApplicationContext

ApplicationContext作为应用上下文，继承自Context，提供了应用生命周期监听、进程管理、应用环境设置等应用级别的管控能力。 > **说明：** > > 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** ApplicationContext extends Context

**起始版本：** 23

<!--Device-unnamed-declare class ApplicationContext--><!--Device-unnamed-declare class ApplicationContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(): Promise<Array<ProcessInformation>>
```

获取运行中的进程信息。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-getProcessRunningInformation(): Promise<Array<ProcessInformation>>--><!--Device-ApplicationContext-getProcessRunningInformation(): Promise<Array<ProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ProcessInformation&gt;&gt; | Promise对象，返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

获取运行中的进程信息。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-getProcessRunningInformation(callback: AsyncCallback<Array<ProcessInformation>>): void--><!--Device-ApplicationContext-getProcessRunningInformation(callback: AsyncCallback<Array<ProcessInformation>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;ProcessInformation&gt;&gt; | 是 | 回调函数，返回有关运行进程的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## preloadUIExtensionAbility

```TypeScript
preloadUIExtensionAbility(want: Want): Promise<void>
```

预加载指定UIExtensionAbility实例。使用Promise异步回调。 被预加载的UIExtensionAbility实例会执行到UIExtensionAbility的onCreate生命周期，然后等待被当前应用正式加载。 被预加载的UIExtensionAbility实例会执行到UIExtensionAbility的onCreate生命周期，然后等待被当前应用正式加载。

**起始版本：** 23

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-preloadUIExtensionAbility(want: Want): Promise<void>--><!--Device-ApplicationContext-preloadUIExtensionAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 预加载UIExtensionAbility的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // 构造预加载UIExtensionAbility的want参数
    let want: Want = {
      bundleName: 'com.ohos.uiextensionprovider',
      abilityName: 'UIExtensionProvider',
      moduleName: 'entry',
      parameters: {
        // 与UIExtensionAbility在module.json5中"type"字段配置一致
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    try {
      // 获取ApplicationContext实例
      let applicationContext = this.context.getApplicationContext();
      // 预加载UIExtensionAbility
      applicationContext.preloadUIExtensionAbility(want)
        .then(() => {
          // 预加载成功处理
          console.info('preloadUIExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // 预加载失败处理
          console.error('preloadUIExtensionAbility failed');
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`preloadUIExtensionAbility failed. code: ${code}, message: ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.ohos.uiextensionprovider',
      abilityName: 'UIExtensionProvider',
      moduleName: 'entry',
      parameters: {
        // 与UIExtensionAbility在module.json5中"type"字段配置一致
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      } as Record<string, RecordData>
    };
    try {
      let applicationContext = this.context.getApplicationContext();
      applicationContext.preloadUIExtensionAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('preloadUIExtensionAbility succeed');
        })
        .catch((err) => {
          // 处理业务逻辑错误
          let code = (err as BusinessError).code;
          let message = (err as BusinessError).message;
          console.error(`preloadUIExtensionAbility failed 1. code: ${code}, message: ${message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`preloadUIExtensionAbility failed 2. code: ${code}, message: ${message}`);
    }
  }
}
```

## registerAbilityLifecycleCallback

```TypeScript
registerAbilityLifecycleCallback(abilityLifecycleCallback: AbilityLifecycleCallback): number
```

注册监听应用内UIAbility的生命周期。使用callback异步回调。 &lt;p&gt;**说明：**: <br>仅支持主线程调用。 &lt;/p&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [on](arkts-ability-applicationcontext-c.md#onabilitylifecycle)(type: 'abilityLifecycle', callback: AbilityLifecycleCallback)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-registerAbilityLifecycleCallback(abilityLifecycleCallback: AbilityLifecycleCallback): number--><!--Device-ApplicationContext-registerAbilityLifecycleCallback(abilityLifecycleCallback: AbilityLifecycleCallback): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityLifecycleCallback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | 是 | UIAbility生命周期变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.unregisterAbilityLifecycleCallback()]{ |

## registerEnvironmentCallback

```TypeScript
registerEnvironmentCallback(environmentCallback: EnvironmentCallback): number
```

注册对系统环境变化的监听。使用callback异步回调。 &lt;p&gt;**说明：**: <br>仅支持主线程调用。 &lt;/p&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [on](arkts-ability-applicationcontext-c.md#onabilitylifecycle)(type: 'environment', callback: EnvironmentCallback)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-registerEnvironmentCallback(environmentCallback: EnvironmentCallback): number--><!--Device-ApplicationContext-registerEnvironmentCallback(environmentCallback: EnvironmentCallback): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| environmentCallback | [EnvironmentCallback](../../apis-na/arkts-apis/arkts-na-app-ability-environmentcallback-environmentcallback-i.md) | 是 | 系统环境变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.unregisterEnvironmentCallback]{ |

## unregisterAbilityLifecycleCallback

```TypeScript
unregisterAbilityLifecycleCallback(callbackId: number, callback: AsyncCallback<void>): void
```

取消监听应用内UIAbility的生命周期。使用callback异步回调。 &lt;p&gt;**说明：**: <br>仅支持主线程调用。 &lt;/p&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [off](arkts-ability-applicationcontext-c.md#offabilitylifecycle)(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-unregisterAbilityLifecycleCallback(callbackId: number, callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-unregisterAbilityLifecycleCallback(callbackId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消监听应用内生命周期成功，err为undefined，否则为错误对象。 |

## unregisterAbilityLifecycleCallback

```TypeScript
unregisterAbilityLifecycleCallback(callbackId: number): Promise<void>
```

取消监听应用内UIAbility的生命周期。使用Promise异步回调。 &lt;p&gt;**说明：**: <br>仅支持主线程调用。 &lt;/p&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** off(type: 'abilityLifecycle', callbackId: number): Promise&lt;void&gt;;

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-unregisterAbilityLifecycleCallback(callbackId: number): Promise<void>--><!--Device-ApplicationContext-unregisterAbilityLifecycleCallback(callbackId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback<void>): void
```

取消对系统环境变化的监听。使用callback异步回调。 &lt;p&gt;**说明：**: <br>仅支持主线程调用。 &lt;/p&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [off](arkts-ability-applicationcontext-c.md#offabilitylifecycle)(type: 'environment', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback<void>): void--><!--Device-ApplicationContext-unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) 接口注册监听系统环境变化时返回的ID。 |
| envcallback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消对系统环境变化的监听成功，err为undefined，否则为错误对象。 |

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number): Promise<void>
```

取消对系统环境变化的监听。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** off(type: 'environment', callbackId: number): Promise&lt;void&gt;;

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-unregisterEnvironmentCallback(callbackId: number): Promise<void>--><!--Device-ApplicationContext-unregisterEnvironmentCallback(callbackId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) 接口注册监听系统环境变化时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

