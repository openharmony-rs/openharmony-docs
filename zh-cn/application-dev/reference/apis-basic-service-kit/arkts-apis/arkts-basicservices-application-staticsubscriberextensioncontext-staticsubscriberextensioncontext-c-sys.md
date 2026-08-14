# StaticSubscriberExtensionContext（系统接口）

StaticSubscriberExtensionContext模块是StaticSubscriberExtensionAbility的上下文环境，继承自ExtensionContext。 StaticSubscriberExtensionContext模块提供StaticSubscriberExtensionAbility具有的接口和能力。

**继承/实现关系：** StaticSubscriberExtensionContext extends ExtensionContext

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class StaticSubscriberExtensionContext--><!--Device-unnamed-declare class StaticSubscriberExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

拉起与静态订阅同属一个应用的Ability。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StaticSubscriberExtensionContext-startAbility(want: Want, callback: AsyncCallback<void>): void--><!--Device-StaticSubscriberExtensionContext-startAbility(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的want信息。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，用于接收启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16300003](../../apis-ability-kit/errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);

    try {
      this.context.startAbility(want, (error: BusinessError) => {
        if (error) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}.`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

拉起与静态订阅同属一个应用的Ability。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StaticSubscriberExtensionContext-startAbility(want: Want): Promise<void>--><!--Device-StaticSubscriberExtensionContext-startAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise形式返回启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16300003](../../apis-ability-kit/errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
    try {
      this.context.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
    try {
      this.context.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${(error.code)}, error.message: ${(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
```

