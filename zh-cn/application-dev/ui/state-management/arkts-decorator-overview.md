# UI装饰器总览
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @s10021109-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan-->
<!--Adviser: @zhang_yixin13-->

ArkUI包含通用的UI装饰器列表如下：

| 通用装饰器                                         | 装饰器说明          |
| -------------------------------------------------- | ------------------- |
| [\@Require](./arkts-require.md)                    | 校验构造传参。      |
| [\@Builder](./arkts-builder.md)                    | 自定义构建函数。    |
| [\@LocalBuilder](./arkts-localBuilder.md)          | 维持组件关系。      |
| [\@BuilderParam](./arkts-builderparam.md)          | 引用\@Builder函数。 |
| [\@Styles](./arkts-style.md)                       | 定义组件重用样式。  |
| [\@Extend](./arkts-extend.md)                      | 定义扩展组件样式。  |
| [\@AnimatableExtend](./arkts-animatable-extend.md) | 定义可动画属性。    |
| [\@Env](../arkts-env-system-property.md)           | 环境变量。          |

ArkUI包含的V1状态管理装饰器列表如下：

| V1状态管理装饰器                                             | 装饰器说明                                   |
| ------------------------------------------------------------ | -------------------------------------------- |
| [\@State](./arkts-state.md)                                  | 基础状态变量。                               |
| [\@Prop](./arkts-prop.md)                                    | 建立父子状态单向同步。                       |
| [\@Link](./arkts-link.md)                                    | 建立父子状态双向同步。                       |
| [\@ObjectLink](./arkts-observed-and-objectlink.md)           | 嵌套类对象属性变化观察。                     |
| [\@Provide](./arkts-provide-and-consume.md)                  | 与后代状态双向同步。                         |
| [\@Consume](./arkts-provide-and-consume.md)                  | 与祖先状态双向同步。                         |
| [\@Watch](./arkts-watch.md)                                  | 状态变量变化监听。                           |
| [\@StorageLink](./arkts-appstorage.md#storagelink)           | 与AppStorage中对应的属性建立单向数据同步。   |
| [\@StoragProp](./arkts-appstorage.md#storageprop)            | 与AppStorage中对应的属性建立双向数据同步。   |
| [\@LocalStoragLink](./arkts-localstorage.md#localstoragelink) | 与LocalStorage中对应的属性建立单向数据同步。 |
| [\@LocalStoragProp](./arkts-localstorage.md#localstorageprop) | 与LocalStorage中对应的属性建立双向数据同步。 |
| [\@Observed](./arkts-observed-and-objectlink.md)             | 标记类可观察。                               |
| [\@Track](./arkts-track.md)                                  | 类对象属性级更新。                           |
| [\@Reusable](./arkts-reusable.md)                            | 标记组件可复用。                             |

ArkUI包含的V2状态管理装饰器列表如下：

| V2状态管理装饰器                                    | 装饰器说明           |
| --------------------------------------------------- | -------------------- |
| [\@Local](./arkts-new-local.md)                     | 组件内部状态。       |
| [\@Param](./arkts-new-param.md)                     | 组件外部输入。       |
| [\@Once](./arkts-new-once.md)                       | 初始化同步一次。     |
| [\@Event](./arkts-new-event.md)                     | 规范组件输出。       |
| [\@Provider](./arkts-new-provider-and-consumer.md)  | 与后代状态双向同步。 |
| [\@Consumer](./arkts-new-provider-and-consumer.md)  | 与祖先状态双向同步。 |
| [\@Monitor](./arkts-new-monitor.md)                 | 状态变量变化监听。   |
| [\@Computed](./arkts-new-computed.md)               | 计算属性。           |
| [\@ObservedV2](./arkts-new-observedV2-and-trace.md) | 标记类可观察         |
| [\@Trace](./arkts-new-observedV2-and-trace.md)      | 标记类属性可观察。   |
| [\@Type](./arkts-new-type.md)                       | 标记类属性的类型。   |
| [\@ReusableV2](./arkts-new-reusableV2.md)           | 标记组件可复用。     |

