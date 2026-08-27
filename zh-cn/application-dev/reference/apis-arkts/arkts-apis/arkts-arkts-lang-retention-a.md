# Retention

```TypeScript
export @interface Retention
```

系统提供的API注解能力，可用于指定自定义注解的生命周期。此注解只能标注在其他注解声明上。在自定义注解上标注Retention注解后，根据policy的不同取值，编译器会对自定义注解执行不同的保留策略。

**起始版本：** 24

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { lang, Retention, RetentionPolicy } from '@kit.ArkTS';
```

## policy

```TypeScript
policy: RetentionPolicy
```

注解的保留策略。

**类型：** [RetentionPolicy](arkts-arkts-lang-retentionpolicy-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang
