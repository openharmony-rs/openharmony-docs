# createModuleContext（系统接口）

## createModuleContext

```TypeScript
export function createModuleContext(context: Context, bundleName: string, moduleName: string): Promise<Context>
```

根据入参Context创建相应模块的Context。使用Promise异步回调。

> **说明：**
>
> - 从API version 18开始，Context支持获取当前应用的进程名
> [processName](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#context)。
> createModuleContext创建的Context中的processName属性与入参Context中的processName属性一致，其他属性根据入参Context、bundleName和moduleName获得相应
> 的属性值。
>
> - 由于创建模块上下文的过程涉及资源查询与初始化，耗时相对较长，在对应用流畅性要求较高的场景下，不建议频繁或多次调用createModuleContext接口创建多个Context实例，以免影响用户体验。

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 表示应用上下文。 |
| bundleName | string | 是 | 表示应用包名。取值为空字符串时，默认为当前应用。 |
| moduleName | string | 是 | 表示应用模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Context&gt; | Promise对象。返回创建的Context。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
import { UIAbility, application, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    let moduleContext: common.Context;
    try {
      application.createModuleContext(this.context, 'bundlename', 'entry').then((data: Context)=>{
        moduleContext = data;
        console.info('createModuleContext success!');
      }).catch((error : BusinessError)=>{
        console.error(`createModuleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
      })
    } catch (error) {
      console.error(`createModuleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}

```

