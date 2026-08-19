# lang

本模块提供ArkTS语言的基础类型定义，支持跨线程传递数据结构、注解保留策略控制等功能。当前提供ISendable类型、RetentionPolicy枚举类型和Retention注解。

**起始版本：** 12

<!--Device-unnamed-declare namespace lang--><!--Device-unnamed-declare namespace lang-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { lang, Retention, RetentionPolicy } from '@kit.ArkTS';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-lang-isendable-i.md) | 是所有Sendable对象类型（除null和undefined）的父类型。实现该接口后，自定义类的实例将支持跨线程传递。自身不定义任何方法和属性。 ArkTS中，ISendable类型的对象是Object类型的实例，遵循Object类型的基本特征，同时支持跨线程传递。 ISendable主要用在开发者自定义Sendable数据结构的场景中。ArkTS语言标准库中的Sendable容器类型（如Array、Map、Set等）隐式地继承并实现了ISendable。 |

