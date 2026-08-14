# ISendable

是所有Sendable对象类型（除null和undefined）的父类型。实现该接口后，自定义类的实例将支持跨线程传递。自身不定义任何方法和属性。 ArkTS中，ISendable类型的对象是Object类型的实例，遵循Object类型的基本特征，同时支持跨线程传递。 ISendable主要用在开发者自定义Sendable数据结构的场景中。ArkTS语言标准库中的Sendable容器类型（如Array、Map、Set等）隐式地继承并实现了ISendable。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-lang-interface ISendable--><!--Device-lang-interface ISendable-End-->

**系统能力：** SystemCapability.Utils.Lang

