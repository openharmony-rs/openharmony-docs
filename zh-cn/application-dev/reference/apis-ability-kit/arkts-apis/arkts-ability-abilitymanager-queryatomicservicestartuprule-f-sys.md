# queryAtomicServiceStartupRule（系统接口）

## queryAtomicServiceStartupRule

```TypeScript
function queryAtomicServiceStartupRule(context: Context, appId: string): Promise<AtomicServiceStartupRule>
```

查询嵌入式拉起[EmbeddableUIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的规则。使用Promise异步回调。 该接口仅在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-function queryAtomicServiceStartupRule(context: Context, appId: string): Promise<AtomicServiceStartupRule>--><!--Device-abilityManager-function queryAtomicServiceStartupRule(context: Context, appId: string): Promise<AtomicServiceStartupRule>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 嵌入式拉起EmbeddableUIAbility的调用方Context。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明**：目前仅支持[UIAbilityContext]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AtomicServiceStartupRule&gt; | Promise对象。返回嵌入式拉起原子化服务的规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { abilityManager, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // 应用的唯一标识
    let appId: string = '6918661953712445909';
    try {
      abilityManager.queryAtomicServiceStartupRule(this.context, appId)
        .then((data: abilityManager.AtomicServiceStartupRule) => {
          console.info(`queryAtomicServiceStartupRule data: ${data}`);
        })
        .catch((e: Error) => {
          let err = e as BusinessError;
          console.error(`queryAtomicServiceStartupRule failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (e) {
      // 处理入参错误异常
      let err = e as BusinessError;
      console.error(`param is invalid, code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

