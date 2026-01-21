# ArkTS方舟编程语言Changelog

## cl.arkcompiler.1 js OOM异常崩溃栈形式变更

**访问级别**

其他

**变更原因**

变更前应用发生js OOM异常时，既可能产生jscrash，也可能产生cppcrash，影响三方生态应用对OOM异常的数据统计。

**变更影响**

此变更不涉及应用适配。

变更前：应用主线程堆发生js OOM异常时产生jscrash，worker/taskpool线程堆发生js OOM异常时产生cppcrash，共享堆发生js OOM异常时，既可能产生jscrash，也可能产生cppcrash。

变更后：应用主线程堆、worker/taskpool线程堆以及共享堆发生js OOM异常时，仅会产生jscrash。

| 线程堆 | 变更前 | 变更后 |
|------|--------|--------|
|主线程堆|jscrash|jscrash|
|worker/taskpool线程堆|cppcrash|jscrash|
|共享堆|jscrash/cppcrash|jscrash|

**起始 API Level**

API 12

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

不涉及

**适配指导**

默认行为变更，开发者需审视此变更是否对自身相关业务代码逻辑产生影响，若有影响需根据自身业务代码进行对应适配。