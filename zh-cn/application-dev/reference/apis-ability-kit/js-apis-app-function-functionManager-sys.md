# @ohos.app.function.functionManager (Function管理)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

Function是定义在应用包中的一个业务逻辑单元，可以接收大模型提供的结构化数据来完成应用定义的功能，例如查询实时天气信息、打开指定应用页面等。

本模块提供Function的管理和调用能力，可以查询可用的Function信息、调用指定的Function执行业务逻辑。

> **说明：**
>
> 本模块接口为系统接口。

**起始版本：** 26.0.0

## 导入模块

```ts
import { functionManager } from '@kit.AbilityKit';
```

## InvokeOptions

Function调用的可选参数。包含Function调用时的应用上下文信息。

**起始版本：** 26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称       | 类型 | 必填 | 说明 |
| ---------- | ---- | --- | ------------------ |
| context | [Context](js-apis-inner-application-context.md) | 否 | 执行Function调用时的应用上下文信息。<br>**说明**：目前仅支持[UIAbilityContext (UIAbility上下文)](js-apis-inner-application-uiAbilityContext.md)<br>默认值：undefined。 |

## InvokeResult

Function调用的结果。包含Function调用成功时返回的数据，调用失败时的错误码和错误信息。

**起始版本：** 26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称          | 类型     | 只读 | 必填 | 说明 |
| ------------- | ------- | ---- | ---  |----------------- |
| success      | boolean  | 是   | 是   | 调用是否成功（业务逻辑层面）。true：调用成功，data字段包含返回数据；false：调用失败，errorCode和errorMsg字段包含错误信息。 |
| data    | any  | 是   | 否   | 调用成功时返回的数据，类型遵循Function定义的返回值类型。仅在success为true时有值。默认值：undefined。 |
| errorCode     | number  | 是   | 否   | 调用失败时的错误码。仅在success为false时有值。默认值：undefined。 |
| errorMsg  | string  | 是   | 否   | 调用失败时的错误描述。仅在success为false时有值。默认值：undefined。 |


## functionManager.queryFunctions

queryFunctions(): Promise\<Array\<FunctionInfo>>

查询所有可用的Function信息，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_FUNCTION

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**返回值：**

| 类型                               | 说明                       |
| ---------------------------------- | -------------------------- |
| Promise\<Array\<[FunctionInfo](js-apis-inner-application-FunctionInfo-sys.md#functioninfo)>> | Promise对象，返回可用Function的信息列表，包含命名空间、名称、版本、描述、输入输出模式等。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { UIAbility, AbilityConstant, Want, common, functionManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  async onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      let functions:common.FunctionInfo[] = await functionManager.queryFunctions();
      hilog.info(0x0000, 'testTag', `queryFunctions success, functions: ${JSON.stringify(functions)}`);
    } catch (error) {
      hilog.error(0x0000, 'testTag', `queryFunctions failed, error: ${JSON.stringify(error)}`);
    }
  }
}
```

## functionManager.invokeFunction

invokeFunction(functionNamespace: string, functionName: string, args: Record\<string, Object\>, options?: InvokeOptions): Promise\<InvokeResult\>

根据Function命名空间和Function名称调用指定的Function，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_FUNCTION

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| functionNamespace | string | 是 | 目标Function的命名空间，与functionName共同确定唯一的Function。 |
| functionName | string | 是 | 目标Function的名称，与functionNamespace共同确定唯一的Function。 |
| args | Record\<string, Object\> | 是 | 符合Function提供方定义格式的输入参数。 |
| options | [InvokeOptions](#invokeoptions) | 否 | Function调用的可选参数。默认值：详见[InvokeOptions](#invokeoptions)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<[InvokeResult](#invokeresult)\> | Promise对象。返回Function调用的结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
| 35600060 | The function does not exist. |
| 35600061 | The function execute failed. |
| 35600062 | The function execute timeout. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit'
import { JSON } from '@kit.ArkTS';
import { functionManager } from '@kit.AbilityKit'

const LOG_TAG = 'testTag';
const LOG_DOMAIN = 0x00;

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button() {
        Text('invokeFunction test')
      }
      .fontSize(36)
      .onClick(async () => {
        try {
          let funcRet = await functionManager.invokeFunction('com.test.demo', 'functionName', {}, {
            context: this.getUIContext().getHostContext()
          });
          if (funcRet.success) {
            hilog.info(LOG_DOMAIN, LOG_TAG, 'invokeFunction success: ' + JSON.stringify(funcRet));
          } else {
            hilog.info(LOG_DOMAIN, LOG_TAG, 'invokeFunction failed: ' + JSON.stringify(funcRet));
          }
        } catch (e) {
          hilog.info(LOG_DOMAIN, LOG_TAG, 'invokeFunction error: ' + JSON.stringify(e));
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## InvokeFunctionParam

Function调用参数，用于Hook拦截。包含Function命名空间、名称、参数和调用选项。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称             | 类型 | 必填 | 说明 |
| ---------------- | ---- | --- | ------------------ |
| functionNamespace | string | 是 | Function的命名空间。 |
| functionName     | string | 是 | Function的名称。 |
| args             | Record\<string, Object\> | 是 | Function的原始输入参数。 |
| invokeOptions    | [InvokeOptions](#invokeoptions) | 否 | 调用选项。默认值：详见[InvokeOptions](#invokeoptions)的具体属性默认值。 |

## FunctionResultWrap

Function结果包装类，用于[onAfterInvokeFunction()](#onafterinvokefunction)回调。包含调用结果。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称   | 类型 | 必填 | 说明 |
| ------ | ---- | --- | ------------------ |
| result | [InvokeResult](#invokeresult) | 是 | Function调用的结果，包含调用是否成功（success）、成功时的返回数据（data）、失败时的错误码（errorCode）和错误信息（errorMsg），详见[InvokeResult](#invokeresult)。在[onAfterInvokeFunction()](#onafterinvokefunction)回调中可读取该字段查看原始调用结果，修改后会将替换后的结果返回给调用方。 |

## FunctionHook

Function调用拦截Hook接口。传入的Hook对象可实现该接口中可选方法的任意子集，系统仅会调用已实现的方法，未实现的方法将被自动跳过。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

### onBeforeInvokeFunction

onBeforeInvokeFunction(param: InvokeFunctionParam): InvokeFunctionParam

Function调用前的回调。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [InvokeFunctionParam](#invokefunctionparam) | 是 | Function调用参数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [InvokeFunctionParam](#invokefunctionparam) | 替换后的调用参数。 |

**示例：**

```ts
import { FunctionHook, InvokeFunctionParam } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const functionHook: FunctionHook = {
  onBeforeInvokeFunction: (param: InvokeFunctionParam): InvokeFunctionParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeInvokeFunction, namespace: ' + param.functionNamespace + ', name: ' + param.functionName);
    // 可在此修改调用参数，例如替换args
    return param;
  }
};
```

### onAfterInvokeFunction

onAfterInvokeFunction(param: FunctionResultWrap): FunctionResultWrap

Function调用后的回调。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [FunctionResultWrap](#functionresultwrap) | 是 | 原始Function调用结果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [FunctionResultWrap](#functionresultwrap) | 修改后的Function调用结果。 |

**示例：**

```ts
import { FunctionHook, FunctionResultWrap } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const functionHook: FunctionHook = {
  onAfterInvokeFunction: (param: FunctionResultWrap): FunctionResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterInvokeFunction, success: ' + param.result.success);
    // 可在此修改调用结果，例如改写result
    return param;
  }
};
```

## functionManager.registerFunctionHook

registerFunctionHook(hook: FunctionHook): Promise\<void\>

注册[FunctionHook](#functionhook)。FunctionHook注册后用于拦截对[invokeFunction()](#functionmanagerinvokefunction)的调用。同一时间只允许注册一个Function Hook，已有Hook注册时再次注册将失败。本接口仅在开发者模式下可用。如需更新已注册的Hook，请先调用[unregisterFunctionHook()](#functionmanagerunregisterfunctionhook)取消注册后再重新注册。Hook对象必须实现[FunctionHook](#functionhook)接口中至少一个可选方法。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| hook | [FunctionHook](#functionhook) | 是 | 实现FunctionHook接口的Hook对象。该对象必须实现至少一个可选方法。 |

**返回值：**

| 类型           | 说明                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 35600034 | The device is not in developer mode.                         |
| 35600035 | A hook is already registered; unregister it first.           |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

// 定义Function Hook对象
const functionHook: FunctionHook = {
  onBeforeInvokeFunction: (param: InvokeFunctionParam): InvokeFunctionParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeInvokeFunction, namespace: ' + param.functionNamespace + ', name: ' + param.functionName);
    // 可在此修改调用参数
    return param;
  },
  onAfterInvokeFunction: (param: FunctionResultWrap): FunctionResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterInvokeFunction, success: ' + param.result.success);
    // 可在此修改调用结果
    return param;
  }
};

export default class FunctionHookTest {
  static async registerHook() {
    try {
      // 注册Function Hook
      await functionManager.registerFunctionHook(functionHook);
      hilog.info(LOG_DOMAIN, LOG_TAG, 'registerFunctionHook success.');
    } catch (error) {
      hilog.error(LOG_DOMAIN, LOG_TAG, `registerFunctionHook failed, errorCode: ${error.code}, message: ${error.message}`);
    }
  }
}
```

## functionManager.unregisterFunctionHook

unregisterFunctionHook(hook: FunctionHook): Promise\<void\>

取消注册已注册的Function Hook。传入的Hook对象必须与调用[registerFunctionHook()](#functionmanagerregisterfunctionhook)时传入的对象相同。若无Hook注册，调用将失败。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| hook | [FunctionHook](#functionhook) | 是 | 要取消注册的Hook对象。 |

**返回值：**

| 类型           | 说明                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 35600036 | No hook is registered; nothing to unregister.               |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { functionManager, FunctionHook, InvokeFunctionParam } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

// functionHook为调用registerFunctionHook时传入的Hook对象
const functionHook: FunctionHook = {
  onBeforeInvokeFunction: (param: InvokeFunctionParam): InvokeFunctionParam => {
    return param;
  }
};

export default class FunctionHookTest {
  static async unregisterHook() {
    try {
      // 取消注册Function Hook
      await functionManager.unregisterFunctionHook(functionHook);
      hilog.info(LOG_DOMAIN, LOG_TAG, 'unregisterFunctionHook success.');
    } catch (error) {
      hilog.error(LOG_DOMAIN, LOG_TAG, `unregisterFunctionHook failed, errorCode: ${error.code}, message: ${error.message}`);
    }
  }
}
```
