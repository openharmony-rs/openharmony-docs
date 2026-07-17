# AtomicServiceStartupRule（系统接口）

嵌入式拉起原子化服务的规则。

**起始版本：** 18

<!--Device-abilityManager-export interface AtomicServiceStartupRule--><!--Device-abilityManager-export interface AtomicServiceStartupRule-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## isEmbeddedAllowed

```TypeScript
isEmbeddedAllowed: boolean
```

是否允许嵌入式拉起原子化服务。true表示允许嵌入式拉起原子化服务，false表示不允许嵌入式拉起原子化服务。

**类型：** boolean

**起始版本：** 18

<!--Device-AtomicServiceStartupRule-isEmbeddedAllowed: boolean--><!--Device-AtomicServiceStartupRule-isEmbeddedAllowed: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## isOpenAllowed

```TypeScript
isOpenAllowed: boolean
```

是否允许拉起原子化服务。true表示允许拉起原子化服务，false表示不允许拉起原子化服务。

**类型：** boolean

**起始版本：** 18

<!--Device-AtomicServiceStartupRule-isOpenAllowed: boolean--><!--Device-AtomicServiceStartupRule-isOpenAllowed: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

