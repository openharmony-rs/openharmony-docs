# FormExtensionContext

FormExtensionContext模块是[FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c.md)的上下文环境，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。 FormExtensionContext模块提供FormExtensionAbility具有的接口和能力。

**继承/实现关系：** FormExtensionContext extends ExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class FormExtensionContext--><!--Device-unnamed-declare class FormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): long
```

将一个Ability与服务类型的Ability绑定。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long--><!--Device-FormExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的ability的信息，如Ability名称，Bundle名称等。 |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、断开或连接失败后的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回一个connectId，后续根据此connectId断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Can not start invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { FormExtensionAbility } from '@kit.FormKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行connectServiceExtensionAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      }
    };
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote; // remote 用于与ServiceExtensionAbility进行通信
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.error(`onFailed, code: ${code}`);
      }
    };

    let connection: number | null = null;
    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
};
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { Want, common, bundleManager } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';

let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行connectServiceExtensionAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      } as Record<string, RecordData>
    };
    const options: common.ConnectOptions = {
      onConnect: (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect: (elementName: bundleManager.ElementName): void => {
        console.info('----------- onDisconnect -----------');
      },
      onFailed: (code: int): void => {
        console.error('----------- onFailed -----------');
      }
    };

    let connection: long | null = null;
    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void
```

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空，使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionContext-disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void--><!--Device-FormExtensionContext-disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 在 [connectServiceExtensionAbility](#connectserviceextensionability)中返回的number。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当Ability与绑定的服务类型的Ability解绑成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

// commRemote为onConnect回调内返回的remote对象，此处定义为null无任何实际意义，仅作示例
let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 实际使用时，connection为connectServiceExtensionAbility中的返回值，此处定义为1无任何实际意义，仅作示例
    let connection: number = 1;

    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
};
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';

// commRemote为onConnect回调内返回的remote对象，此处定义为null无任何实际意义，仅作示例
let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 实际使用时，connection为connectServiceExtensionAbility中的返回值，此处定义为1无任何实际意义，仅作示例
    let connection: long = 1;

    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError | null) => {
        commRemote = null;
        if (error) {
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: long): Promise<void>
```

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空(Promise形式返回结果)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionContext-disconnectServiceExtensionAbility(connection: long): Promise<void>--><!--Device-FormExtensionContext-disconnectServiceExtensionAbility(connection: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 在 [connectServiceExtensionAbility](#connectserviceextensionability)中返回的number。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

// commRemote为onConnect回调内返回的remote对象，此处定义为null无任何实际意义，仅作示例
let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 实际使用时，connection为connectServiceExtensionAbility中的返回值，此处定义为1无任何实际意义，仅作示例
    let connection: number = 1;

    try {
      this.context.disconnectServiceExtensionAbility(connection)
        .then(() => {
          commRemote = null;
          // 执行正常业务
          console.info('disconnectServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          commRemote = null;
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
};
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';

// commRemote为onConnect回调内返回的remote对象，此处定义为null无任何实际意义，仅作示例
let commRemote: rpc.IRemoteObject | null = null;

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 实际使用时，connection为connectServiceExtensionAbility中的返回值，此处定义为1无任何实际意义，仅作示例
    let connection: long = 1;

    try {
      this.context.disconnectServiceExtensionAbility(connection)
        .then(() => {
          commRemote = null;
          // 执行正常业务
          console.info('disconnectServiceExtensionAbility succeed');
        })
        .catch((err) => {
          let error = err as BusinessError;
          commRemote = null;
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

拉起一个应用的Ability。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionContext-startAbility(want: Want, callback: AsyncCallback<void>): void--><!--Device-FormExtensionContext-startAbility(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 包含bundleName，abilityName以及用户自定义参数用于拉起Ability。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当拉起一个应用的Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | An IPC connection error happened. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| 16500101 | The application is not a system application.<br>**适用版本：** 9 - 11 |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId: ${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      }
    };
    this.context.startAbility(want, (error: BusinessError) => {
      if (error) {
        console.error(`FormExtensionContext startAbility, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
      } else {
        console.info('FormExtensionContext startAbility success');
      }
    });
  }
};
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId: ${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      } as Record<string, RecordData>
    };
    this.context.startAbility(want, (error: BusinessError | null) => {
      if (error) {
        console.error(`FormExtensionContext startAbility, error: code: ${error.code} message: ${error.message}`);
      } else {
        console.info('FormExtensionContext startAbility success');
      }
    });
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

拉起一个应用的Ability。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionContext-startAbility(want: Want): Promise<void>--><!--Device-FormExtensionContext-startAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 包含bundleName，abilityName以及用户自定义参数用于拉起Ability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | An IPC connection error happened. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| 16500101 | The application is not a system application.<br>**适用版本：** 9 - 11 |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      }
    };
    this.context.startAbility(want).then(() => {
      console.info('StartAbility Success');
    }).catch((error: BusinessError) => {
      console.error(`StartAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
};
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      } as Record<string, RecordData>
    };
    this.context.startAbility(want).then(() => {
      console.info('StartAbility Success');
    }).catch((error) => {
      console.error(`StartAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

