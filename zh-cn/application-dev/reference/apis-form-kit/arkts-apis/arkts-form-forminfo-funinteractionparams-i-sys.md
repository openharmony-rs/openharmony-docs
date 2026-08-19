# FunInteractionParams（系统接口）

趣味交互卡片配置参数。

**起始版本：** 23

<!--Device-formInfo-interface FunInteractionParams--><!--Device-formInfo-interface FunInteractionParams-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName?: string
```

趣味交互场景 extensionAbility 名称，默认为空。

**类型：** string

**起始版本：** 23

<!--Device-FunInteractionParams-abilityName?: string--><!--Device-FunInteractionParams-abilityName?: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## keepStateDuration

```TypeScript
keepStateDuration?: int
```

趣味交互场景无交互时，激活态保持时长。默认值为10000，单位ms。取值为(0,60000]的整数，超过取值范围则取最大值60000。 **说明：** 在API版本26.0.0之前该字段为(0,10000]的整数，超过取值范围则取默认值10000。

**类型：** int

**起始版本：** 23

<!--Device-FunInteractionParams-keepStateDuration?: int--><!--Device-FunInteractionParams-keepStateDuration?: int-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## subBundleName

```TypeScript
subBundleName: string
```

趣味交互场景 [独立分包名](https://developer.huawei.com/consumer/cn/doc/quickApp-Guides/quickgame-independent-subpackage-0000002076341729)。

**类型：** string

**起始版本：** 23

<!--Device-FunInteractionParams-subBundleName: string--><!--Device-FunInteractionParams-subBundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## targetBundleName

```TypeScript
targetBundleName: string
```

趣味交互场景 [主包包名](https://developer.huawei.com/consumer/cn/doc/quickApp-Guides/quickgame-independent-subpackage-0000002076341729)。

**类型：** string

**起始版本：** 23

<!--Device-FunInteractionParams-targetBundleName: string--><!--Device-FunInteractionParams-targetBundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

