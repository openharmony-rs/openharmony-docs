# @arkts.lang

本模块提供ArkTS语言的基础类型定义，支持跨线程传递数据结构、注解保留策略控制等功能。当前提供ISendable类型、RetentionPolicy枚举类型和Retention注解。

## 导入模块

```TypeScript
import { lang, Retention, RetentionPolicy } from '@kit.ArkTS';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [lang](arkts-arkts-lang-n.md) | 本模块提供ArkTS语言的基础类型定义，支持跨线程传递数据结构、注解保留策略控制等功能。当前提供ISendable类型、RetentionPolicy枚举类型和Retention注解。 |

### 注解

| 名称 | 说明 |
| --- | --- |
| [Retention](arkts-arkts-lang-retention-a.md) | 系统提供的API注解能力，可用于指定自定义注解的生命周期。此注解只能标注在其他注解声明上。在自定义注解上标注Retention注解后，根据policy的不同取值，编译器会对自定义注解执行不同的保留策略。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RetentionPolicy](arkts-arkts-lang-retentionpolicy-e.md) | 描述注解类型保留策略的枚举类型。其枚举值和Retention结合使用，以指定注解的生命周期。 |
