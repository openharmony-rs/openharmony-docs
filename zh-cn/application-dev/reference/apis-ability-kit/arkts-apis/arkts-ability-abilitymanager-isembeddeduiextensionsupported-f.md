# isEmbeddedUIExtensionSupported

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

<a id="isembeddeduiextensionsupported"></a>
## isEmbeddedUIExtensionSupported

```TypeScript
function isEmbeddedUIExtensionSupported(): boolean
```

开发者通过调用该接口判断[EmbeddedUIExtensionAbility](docroot://application-models/embeddeduiextensionability.md)是否可以在当前设备上使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-function isEmbeddedUIExtensionSupported(): boolean--><!--Device-abilityManager-function isEmbeddedUIExtensionSupported(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持[EmbeddedUIExtensionAbility](docroot://application-models/embeddeduiextensionability.md)。返回true表示当前设备支持；返回false表示当前设备不支持。 |

**示例：**

```TypeScript
import { abilityManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // 判断当前设备是否支持EmbeddedUIExtensionAbility
    let isSupported: boolean = abilityManager.isEmbeddedUIExtensionSupported();
    console.info(`isEmbeddedUIExtensionSupported is ${isSupported}`);
  }
}

```

