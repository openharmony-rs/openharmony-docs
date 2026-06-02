# Atomics模块描述
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

Atomics用于解决多线程并发编程中的竞态条件问题，确保对共享数据的并发操作安全。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
> - 基于typedArray的静态Atomics接口主要为兼容保留，不再作为推荐用法。新开发应优先使用更符合ArkTS-Sta设计规范的实例化原子类型接口。

Atomics相关能力按接口形态划分为以下两部分：
- [实例化原子类型接口](arkts-sta-atomics.md)：通过原子类实例直接对单个共享值或对象引用执行原子操作。介绍AtomicReference\<T>、AtomicInt、AtomicLong、AtomicShort、AtomicByte、AtomicFloat、AtomicDouble、AtomicChar和AtomicBoolean的构造函数及成员方法。
- [Atomics (基于typedArray的原子类型接口)](arkts-sta-legacyatomics.md)：该接口通过静态方法对基于ArrayBuffer构建的typedArray执行原子操作，当前主要为兼容保留，不再作为推荐用法。新开发应优先使用实例化原子类型接口。
