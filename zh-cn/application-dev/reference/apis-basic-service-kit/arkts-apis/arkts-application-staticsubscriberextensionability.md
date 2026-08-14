# @ohos.application.StaticSubscriberExtensionAbility

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StaticSubscriberExtensionAbility](arkts-basicservices-application-staticsubscriberextensionability-staticsubscriberextensionability-c-sys.md) | 本模块是 BasicServicesKit 提供的静态订阅扩展能力基类，用于实现静态公共事件订阅。 静态订阅是一种无需应用常驻运行即可接收公共事件的订阅方式。该能力适用于系统服务 或系统应用需要在特定公共事件发生时执行后台处理的场景。 `StaticSubscriberExtensionAbility`基类提供两个关键成员：`onReceiveEvent`方法与 `context`属性。`context`属性类型为 StaticSubscriberExtensionContext，是扩展能力的 运行上下文，继承自`ExtensionContext`，提供`startAbility`方法用于在事件处理过程中 拉起同应用内的其他 Ability。 **API 组合使用关系说明：** 本模块典型使用流程为"继承基类 → 重写`onReceiveEvent` → 系统拉起回调 → 读取事件 数据 → 拉起目标 Ability"。需注意，`context.startAbility`仅能拉起与当前 `StaticSubscriberExtensionAbility`属于同一应用的 Ability。 |
<!--DelEnd-->

