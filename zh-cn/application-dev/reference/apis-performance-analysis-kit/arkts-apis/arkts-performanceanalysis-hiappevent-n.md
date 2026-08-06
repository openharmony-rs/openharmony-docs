# hiAppEvent

本模块提供应用打点和事件订阅能力，包括事件存储、事件订阅、事件清理、打点配置等功能。HiAppEvent将应用运行过程中触发的事件信息统一归纳到[AppEventInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 中，并将事件分为系统事件和应用事件两类。 系统事件来源于系统服务，是系统预先定义的事件，这类事件信息中的事件参数对象params包含的字段已由各系统事件定义，具体字段含义在各系统事件指南的介绍中，例如 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 应用事件来源于应用，是应用开发者自己定义的事件，这类事件信息支持自定义后通过[Write]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_打点接口进行配置设定，具体字段含义可结合开发者需求展开。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace hiAppEvent--><!--Device-unnamed-declare namespace hiAppEvent-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [domain](arkts-performanceanalysis-hiappevent-domain-n.md) | 提供域名常量。 \|名称\|类型\|只读\|描述\| \| --- \| ------ \| ------ \| ---------- \| \| OS \| string \|是\|系统域\| |
| [event](arkts-performanceanalysis-hiappevent-event-n.md) | 提供事件名称常量，包括系统事件名称常量和应用事件名称常量。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_应用事件名称常量是为开发者在调用Write接口进行应用事件打点时预留的可选自定义事件名称。 |
| [param](arkts-performanceanalysis-hiappevent-param-n.md) | 提供参数名常量。 \|名称\|类型\|只读\|描述\| \| ------------------------------- \| ------ \| ------ \| ------------------ \| \| USER\_\_\_ESCAPED\_UNDERSCORE\_\_\_ID \| string \|是\|自定义用户ID\| \| DISTRIBUTED\_\_\_ESCAPED\_UNDERSCORE\_\_\_SERVICE\_\_\_ESCAPED\_UNDERSCORE\_\_\_NAME \| string \|是\|分布式服务名称\| \| DISTRIBUTED\_\_\_ESCAPED\_UNDERSCORE\_\_\_SERVICE\_\_\_ESCAPED\_UNDERSCORE\_\_\_INSTANCE\_\_\_ESCAPED\_UNDERSCORE\_\_\_ID \| string \|是\|分布式服务实例ID\| |

### 函数

| 名称 | 说明 |
| --- | --- |
| [configure](arkts-performanceanalysis-hiappevent-configure-f.md#configure) | 应用事件打点配置方法，支持配置打点开关和目录存储配额大小。 |
| [write](arkts-performanceanalysis-hiappevent-write-f.md#write) | 应用事件打点方法，将AppEventInfo类型的事件进行存储，使用Promise方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入 系统事件（[Event]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）进行处理。 |
| [write](arkts-performanceanalysis-hiappevent-write-f.md#write-1) | 应用事件打点方法，将AppEventInfo类型的事件进行存储，使用callback方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入 系统事件（[Event]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）进行订阅。 |
| [setEventParam](arkts-performanceanalysis-hiappevent-seteventparam-f.md#seteventparam) | 事件自定义参数设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过事件领域和事件名称关联系统事件和应用事件。 |
| [setEventConfig](arkts-performanceanalysis-hiappevent-seteventconfig-f.md#seteventconfig) | 事件相关的配置参数设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过事件名称，设置事件相关的配置参数。 不同的事件有不同的配置项，目前仅支持以下事件： - MAIN\_\_\_ESCAPED\_UNDERSCORE\_\_\_THREAD\_\_\_ESCAPED\_UNDERSCORE\_\_\_JANK（参数配置详见 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_） - APP\_\_\_ESCAPED\_UNDERSCORE\_\_\_CRASH（参数配置详见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_） - RESOURCE\_\_\_ESCAPED\_UNDERSCORE\_\_\_OVERLIMIT（参数配置详见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_） |
| [addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md#addwatcher) | 添加事件观察者。可通过事件观察者的回调函数监听事件。 |
| [removeWatcher](arkts-performanceanalysis-hiappevent-removewatcher-f.md#removewatcher) | 移除事件观察者。 |
| [clearData](arkts-performanceanalysis-hiappevent-cleardata-f.md#cleardata) | 应用事件打点数据清理方法，将当前应用存储在本地的打点数据进行清除。 |
| [setUserId](arkts-performanceanalysis-hiappevent-setuserid-f.md#setuserid) | 设置用户ID值。用于在配置[Processor]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_数据处理者时进行关联。 |
| [getUserId](arkts-performanceanalysis-hiappevent-getuserid-f.md#getuserid) | 获取通过setUserId接口设置的value值。 |
| [setUserProperty](arkts-performanceanalysis-hiappevent-setuserproperty-f.md#setuserproperty) | 设置用户属性值。用于在配置[Processor]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_数据处理者时进行关联。 |
| [getUserProperty](arkts-performanceanalysis-hiappevent-getuserproperty-f.md#getuserproperty) | 获取通过setUserProperty接口设置的value值。 |
| [addProcessor](arkts-performanceanalysis-hiappevent-addprocessor-f.md#addprocessor) | 添加数据处理者配置信息，用于配置处理者接收的事件名等信息。事件发生后处理者可以接收事件。 该接口为同步接口，包含耗时操作。为了确保性能，建议使用[addProcessorFromConfig]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_异步接口或者交由子线程执行。 |
| [addProcessorFromConfig](arkts-performanceanalysis-hiappevent-addprocessorfromconfig-f.md#addprocessorfromconfig) | 添加数据处理者配置信息，通过配置文件配置处理者接收的事件名等信息，事件发生后处理者可以接收事件，使用Promise异步回调。 |
| [removeProcessor](arkts-performanceanalysis-hiappevent-removeprocessor-f.md#removeprocessor) | 移除上报事件的数据处理者。 |
| [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md#configeventpolicy) | 系统事件相关的配置策略设置方法，使用Promise方式作为异步回调。 在同一生命周期中，可以通过配置策略设置系统事件相关的策略参数。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | 订阅数据持有者类，用于对事件信息进行处理。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConfigOption](arkts-performanceanalysis-hiappevent-configoption-i.md) | 提供对应用事件打点功能的配置选项。 |
| [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | 提供事件信息的参数选项。 |
| [AppEventPackage](arkts-performanceanalysis-hiappevent-appeventpackage-i.md) | 提供订阅返回的事件包的参数定义。可用于获取事件包的详细信息，事件包由[takeNext]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口获得。 |
| [TriggerCondition](arkts-performanceanalysis-hiappevent-triggercondition-i.md) | 提供设置[Watcher]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的onTrigger回调触发条件的参数选项。 |
| [AppEventFilter](arkts-performanceanalysis-hiappevent-appeventfilter-i.md) | 提供设置[Watcher]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的订阅过滤条件的参数选项。用于在事件观察者中设置事件过滤条件，确保只有满足过滤条件的事件才会被监听处理。 |
| [AppEventGroup](arkts-performanceanalysis-hiappevent-appeventgroup-i.md) | 提供订阅返回的事件组的参数定义。可用于获取事件组的详细信息，事件组常在[Watcher]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的onReceive回调中使用。 |
| [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md) | 提供事件观察者的参数选项。用于配置和管理事件的观察者，实现对特定事件的监听和处理。 |
| [AppEventReportConfig](arkts-performanceanalysis-hiappevent-appeventreportconfig-i.md) | 数据处理者可以上报事件的描述配置。 |
| [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) | 可以上报事件的数据处理者对象。用于事件的上报和管理，开发者可自定义数据处理配置，满足不同的数据处理需求。 |
| [MainThreadJankPolicy](arkts-performanceanalysis-hiappevent-mainthreadjankpolicy-i.md) | 提供主线程超时事件配置策略的定义。 |
| [CpuUsageHighPolicy](arkts-performanceanalysis-hiappevent-cpuusagehighpolicy-i.md) | 提供CPU高负载事件配置策略的定义。 > **注意：** > > 该接口被调用后，会将设置值持久化。后续重复调用该接口时，若不设置对应参数，则取上一次系统取用的值。 |
| [AppCrashPolicy](arkts-performanceanalysis-hiappevent-appcrashpolicy-i.md) | 提供崩溃事件配置策略的定义。 |
| [AppFreezePolicy](arkts-performanceanalysis-hiappevent-appfreezepolicy-i.md) | 提供应用冻屏事件配置策略的定义。 |
| [ResourceOverlimitPolicy](arkts-performanceanalysis-hiappevent-resourceoverlimitpolicy-i.md) | 提供资源泄漏事件配置策略的定义。 |
| [AddressSanitizerPolicy](arkts-performanceanalysis-hiappevent-addresssanitizerpolicy-i.md) | 提供地址越界事件配置策略的定义。 |
| [EventPolicy](arkts-performanceanalysis-hiappevent-eventpolicy-i.md) | 提供系统事件配置策略的定义，用于使用[configEventPolicy]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_设置事件配置策略。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventType](arkts-performanceanalysis-hiappevent-eventtype-e.md) | 事件类型枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md) | 事件自定义参数值的类型。 |

