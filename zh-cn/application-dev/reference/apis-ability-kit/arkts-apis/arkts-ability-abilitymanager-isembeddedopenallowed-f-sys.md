# isEmbeddedOpenAllowed（系统接口）

## isEmbeddedOpenAllowed

```TypeScript
function isEmbeddedOpenAllowed(context: Context, appId: string): Promise<boolean>
```

判断是否允许嵌入式拉起[EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md#EmbeddableUIAbility)。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 嵌入式拉起EmbeddableUIAbility的调用方Context。 |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示允许嵌入式启动；返回false表示不允许嵌入式启动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

**示例：**

```TypeScript
import { abilityManager, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let appId: string = '6918661953712445909';
    try {
      abilityManager.isEmbeddedOpenAllowed(this.context, appId).then((data) => {
        console.info(`isEmbeddedOpenAllowed data: ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        console.error(`isEmbeddedOpenAllowed failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      console.error(`param is invalid, code is ${err.code}, message is ${err.message}`);
    }
  }
}

```

