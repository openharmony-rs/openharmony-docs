# @ohos.hiviewdfx.hiAppEvent (应用事件打点)

本模块提供应用打点和事件订阅能力，包括事件存储、事件订阅、事件清理、打点配置等功能。HiAppEvent将应用运行过程中触发的事件信息统一归纳到[AppEventInfo](#appeventinfo)中，并将事件分为系统事件和应用事件两类。

系统事件来源于系统服务，是系统预先定义的事件，这类事件信息中的事件参数对象params包含的字段已由各系统事件定义，具体字段含义在各系统事件指南的介绍中，例如[崩溃事件介绍](../../dfx/hiappevent-watcher-crash-events.md)。

应用事件来源于应用，是应用开发者自己定义的事件，这类事件信息支持自定义后通过[Write](#hiappeventwrite-1)打点接口进行配置设定，具体字段含义可结合开发者需求展开。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```


## hiAppEvent.addWatcher

addWatcher(watcher: Watcher): AppEventPackageHolder

添加事件观察者。可通过事件观察者的回调函数监听事件。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名  | 类型                 | 必填 | 说明             |
| ------- | -------------------- | ---- | ---------------- |
| watcher | [Watcher](#watcher) | 是   | 事件观察者。 |

**返回值：**

| 类型                                             | 说明                                 |
| ------------------------------------------------ | ------------------------------------ |
| [AppEventPackageHolder](#appeventpackageholder) | 订阅数据持有者。订阅失败时返回null。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                        |
| -------- | ------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11102001 | Invalid watcher name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11102002 | Invalid filtering event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11102003 | Invalid row value. Possible caused by the row value is less than zero. |
| 11102004 | Invalid size value. Possible caused by the size value is less than zero. |
| 11102005 | Invalid timeout value. Possible caused by the timeout value is less than zero. |

**示例：**

根据添加的事件观察者类型，目前有如下三种使用方法：

方法一：设置回调条件triggerCondition，实现onTrigger()回调。当满足回调条件时，系统将自动触发回调。
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addWatcher({
  name: "watcher1",
  // 订阅过滤条件，这里是订阅了系统事件领域的应用崩溃事件
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
  // 设置触发onTrigger回调的条件，这里是当满足事件总数量达到10个或事件总大小达到1000byte或事件发生超过30s时会触发回调
  triggerCondition: {
    row: 10,
    size: 1000,
    timeOut: 1
  },
  // 实现onTrigger回调，结合triggerCondition使用，满足回调条件触发回调，接收到回调通知后，使用takeNext()查询订阅的事件
  onTrigger: (curRow: number, curSize: number, holder: hiAppEvent.AppEventPackageHolder) => {
    if (holder == null) {
      hilog.error(0x0000, 'hiAppEvent', "holder is null");
      return;
    }
    hilog.info(0x0000, 'hiAppEvent', `curRow=${curRow}, curSize=${curSize}`);
    let eventPkg: hiAppEvent.AppEventPackage | null = null;
    while ((eventPkg = holder.takeNext()) != null) {
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.packageId=${eventPkg.packageId}`);
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.row=${eventPkg.row}`);
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.size=${eventPkg.size}`);
      for (const eventInfo of eventPkg.data) {
        hilog.info(0x0000, 'hiAppEvent', `eventPkg.data=${eventInfo}`);
      }
    }
  }
});
```

方法二：未设置回调条件参数，使用事件订阅返回的holder对象主动获取监听的事件。
<br>针对异常退出时产生的崩溃事件（hiAppEvent.event.APP_CRASH）和应用冻屏事件（hiAppEvent.event.APP_FREEZE），系统捕获维测日志有一定耗时，典型情况下30s内完成，极端情况下2min左右完成。
<br>在手动处理订阅事件的方法中，由于事件可能未生成或日志信息未抓取完成，建议在进程启动后延时重试调用takeNext()获取此类事件。

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

let holder: hiAppEvent.AppEventPackageHolder = hiAppEvent.addWatcher({
  name: "watcher2",
  // 订阅过滤条件，这里是订阅了系统事件领域的应用崩溃事件
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
});
// 通过订阅数据持有者holder，主动获取崩溃事件
if (holder != null) {
  let eventPkg: hiAppEvent.AppEventPackage | null = null;
  while ((eventPkg = holder.takeNext()) != null) {
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.packageId=${eventPkg.packageId}`);
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.row=${eventPkg.row}`);
    hilog.info(0x0000, 'hiAppEvent', `eventPkg.size=${eventPkg.size}`);
    for (const eventInfo of eventPkg.data) {
      hilog.info(0x0000, 'hiAppEvent', `eventPkg.data=${eventInfo}`);
    }
  }
}
```

方法三：实现onReceive()回调，当监听的事件发生后实时触发回调。

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addWatcher({
  name: "watcher3",
  // 订阅过滤条件，这里是订阅了系统事件领域的应用崩溃事件
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
      names: [hiAppEvent.event.APP_CRASH]
    }
  ],
  // 实现onReceive回调，监听到事件后实时回调
  onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
    hilog.info(0x0000, 'hiAppEvent', `domain=${domain}`);
    for (const eventGroup of appEventGroups) {
      hilog.info(0x0000, 'hiAppEvent', `eventName=${eventGroup.name}`);
      for (const eventInfo of eventGroup.appEventInfos) {
        hilog.info(0x0000, 'hiAppEvent', `event=${JSON.stringify(eventInfo)}`, );
      }
    }
  }
});
```


## hiAppEvent.removeWatcher

removeWatcher(watcher: Watcher): void

移除事件观察者。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名  | 类型                 | 必填 | 说明             |
| ------- | -------------------- | ---- | ---------------- |
| watcher | [Watcher](#watcher) | 是   | 事件观察者。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息              |
| -------- | --------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11102001 | Invalid watcher name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |

**示例：**

```ts
// 1. 定义一个事件观察者
let watcher: hiAppEvent.Watcher = {
  name: "watcher1",
}

// 2. 添加一个事件观察者来订阅事件
hiAppEvent.addWatcher(watcher);

// 3. 移除该事件观察者以取消订阅事件
hiAppEvent.removeWatcher(watcher);
```


## hiAppEvent.setEventParam<sup>12+</sup>

setEventParam(params: Record&lt;string, ParamType&gt;, domain: string, name?: string): Promise&lt;void&gt;

事件自定义参数设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过事件领域和事件名称关联系统事件和应用事件，系统事件仅支持[崩溃事件](../../dfx/hiappevent-watcher-crash-events.md)、[应用冻屏事件](../../dfx/hiappevent-watcher-freeze-events.md)和[资源泄漏事件](../../dfx/hiappevent-watcher-resourceleak-events.md)下的js内存泄漏事件。


**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型                           | 必填 | 说明           |
| ------ | ------------------------------ | ---- | -------------- |
| params | Record&lt;string, [ParamType](#paramtype12)&gt; | 是 | 事件自定义参数对象。参数名和参数值规格定义如下：<br>- 参数名为string类型，首字符必须为字母字符或$字符。中间字符必须为数字字符、字母字符或下划线字符。结尾字符必须为数字字符或字母字符。长度非空且不超过32个字符。<br>- 参数值为[ParamType](#paramtype12)类型，参数值长度需在1024个字符以内。<br>- 参数个数需在64个以内。 |
| domain | string                        | 是 | 事件领域。事件领域可支持关联应用事件和系统事件（hiAppEvent.domain.OS）。 |
| name   | string                        | 否 | 事件名称。默认为空字符串，空字符串表示关联事件领域下的所有事件名称。事件名称可支持关联应用事件和系统事件，其中系统事件仅支持关联崩溃事件（hiAppEvent.event.APP_CRASH）和应用冻屏事件（hiAppEvent.event.APP_FREEZE）。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11100001 | Function disabled. Possible caused by the param disable in ConfigOption is true. |
| 11101001 | Invalid event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101002 | Invalid event name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101004 | Invalid string length of the event parameter. |
| 11101005 | Invalid event parameter name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101007 | The number of parameter keys exceeds the limit. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let params: Record<string, hiAppEvent.ParamType> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 给应用事件追加自定义参数
hiAppEvent.setEventParam(params, "test_domain", "test_event").then(() => {
  hilog.info(0x0000, 'hiAppEvent', `success to set event param`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});
```


## hiAppEvent.setEventConfig<sup>15+</sup>

setEventConfig(name: string, config: Record&lt;string, ParamType&gt;): Promise&lt;void&gt;

事件相关的配置参数设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过事件名称，设置事件相关的配置参数。<br/>不同的事件有不同的配置项，目前仅支持MAIN_THREAD_JANK（参数配置详见[主线程超时事件检测](../../dfx/hiappevent-watcher-mainthreadjank-events.md#自定义参数)）和APP_CRASH（参数配置详见[崩溃日志配置参数设置介绍](../../dfx/hiappevent-watcher-crash-events.md#崩溃日志规格自定义参数设置)）事件。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型                           | 必填 | 说明           |
| ------ | ------------------------------ | ---- | -------------- |
| name   | string                        | 是 | 事件名称。 |
| config | Record<string, ParamType> | 是 | 事件自定义参数对象。参数名和参数值规格定义如下：<br>- 参数名为string类型，要求非空，且参数名长度需在1024个字符以内。<br>- 参数值为ParamType类型，参数值长度需在1024个字符以内。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

以下示例用于模拟配置MAIN_THREAD_JANK事件的采集堆栈自定义参数：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let params: Record<string, hiAppEvent.ParamType> = {
  "log_type": "1",
  "sample_interval": "100",
  "ignore_startup_time": "11",
  "sample_count": "21",
  "report_times_per_app": "3"
};
hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
  hilog.info(0x0000, 'hiAppEvent', `Successfully set sampling stack parameters.`);
}).catch((err: BusinessError) => {
hilog.error(0x0000, 'hiAppEvent', `Failed to set sample stack value. Code: ${err.code}, message: ${err.message}`);
});
```

## Watcher

提供事件观察者的参数选项。用于配置和管理事件的观察者，实现对特定事件的监听和处理。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称             | 类型                                                |  只读  | 可选 | 说明                                                         |
| ---------------- | ----------------------------------------------------|------ | ---- | ------------------------------------------------------------ |
| name             | string                                              |  否   | 否   | 观察者名称，用于唯一标识观察者。首字符必须为字母字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。如testName1、crash_Watcher等。                             |
| triggerCondition | [TriggerCondition](#triggercondition)               |  否   | 是   | 订阅回调触发条件，需要与回调函数onTrigger一同传入才会生效。默认不触发。           |
| appEventFilters  | [AppEventFilter](#appeventfilter)[]                 |  否   | 是   | 订阅过滤条件，在需要对订阅事件进行过滤时传入。默认不过滤事件。               |
| onTrigger        | (curRow: number, curSize: number, holder: [AppEventPackageHolder](#appeventpackageholder)) => void |  否   | 是   | 订阅回调函数，需要与回调触发条件triggerCondition一同传入才会生效，函数入参说明如下：<br>curRow：在本次回调触发时的订阅事件总数量； <br>curSize：在本次回调触发时的订阅事件总大小，单位为byte；  <br/>holder：订阅数据持有者对象，可以通过其对订阅事件进行处理。 |
| onReceive<sup>11+</sup>        | (domain: string, appEventGroups: Array<[AppEventGroup](#appeventgroup11)>) => void |  否   | 是 | 订阅实时回调函数，与回调函数onTrigger同时存在时，只触发此回调，函数入参说明如下：<br>domain：回调事件的领域名称； <br>appEventGroups：回调事件集合。 |


## TriggerCondition

提供设置[Watcher](#watcher)的onTrigger回调触发条件的参数选项。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称    | 类型   | 只读 | 可选 | 说明                                   |
| ------- | ------ | ---- | ---- | -------------------------------------- |
| row     | number | 否 | 是   | 满足触发回调的事件总数量，正整数。默认值0，不触发回调。传入负值时，会被置为默认值。             |
| size    | number | 否 | 是   | 满足触发回调的事件总大小，正整数，单位为byte。默认值0，不触发回调。传入负值时，会被置为默认值。 |
| timeOut | number | 否 | 是   | 满足触发回调的超时时长，正整数，单位为30s。默认值0，不触发回调。传入负值时，会被置为默认值。    |


## AppEventFilter

提供设置[Watcher](#watcher)的订阅过滤条件的参数选项。用于在事件观察者中设置事件过滤条件，确保只有满足过滤条件的事件才会被监听处理。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称       | 类型                      | 只读 | 可选 | 说明                     |
| ---------- | ------------------------- | ---- | ---- | ------------------------ |
| domain     | string                    | 否 | 否   | 需要订阅的事件领域。可以是系统事件领域（hiAppEvent.domain.OS）或开发者在使用[Write](#hiappeventwrite-1)接口时传入的自定义事件信息（[AppEventInfo](#appeventinfo)）中的事件领域。     |
| eventTypes | [EventType](#eventtype)[] | 否 | 是   | 需要订阅的事件类型集合。默认不进行过滤。 |
| names<sup>11+</sup>      | string[]                  | 否 | 是   | 需要订阅的事件名称集合。默认不进行过滤。 |

> **说明：**
>
> 系统事件中：地址越界事件和任务执行超时事件不支持在元服务中订阅。启动耗时事件、滑动丢帧事件、CPU高负载事件和24h功耗器件分解统计事件均不支持在元服务和分身应用中订阅。

## AppEventPackageHolder

订阅数据持有者类，用于对事件信息进行处理。

### constructor

constructor(watcherName: string)

类构造函数，用于创建订阅数据持有者实例。先通过[addWatcher](#hiappeventaddwatcher)添加事件观察者，再通过观察者名称关联到应用内已添加的观察者对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型              | 必填 | 说明                     |
| ------ | ----------------- | ---- | ------------------------ |
| watcherName | string | 是   | 已通过[addWatcher](#hiappeventaddwatcher)添加的事件观察者名称。若未通过addWatcher添加，则默认无数据。 |

**示例：**

```ts
// 添加数据观察者“Watcher1”，订阅监听系统事件
hiAppEvent.addWatcher({
  name: "Watcher1",
  appEventFilters: [
    {
      domain: hiAppEvent.domain.OS,
    }
  ],
  });

// 创建订阅数据持有者实例，holder1持有的数据为上述addWatcher中添加的观察者“Watcher1”监听到的事件
let holder1: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
```

### setSize

setSize(size: number): void

设置每次取出的事件包的数据大小阈值。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型   | 必填 | 说明                                         |
| ------ | ------ | ---- | -------------------------------------------- |
| size   | number | 是   | 数据大小阈值，单位为byte。取值范围[0, 2^31-1]，超出范围会抛异常。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息            |
| -------- | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11104001 | Invalid size value. Possible caused by the size value is less than or equal to zero. |

**示例：**

```ts
// 创建订阅数据持有者实例，holder2持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder2: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 设置每次取出事件包的数据大小阈值为1000byte
holder2.setSize(1000);
```

### setRow<sup>12+</sup>

setRow(size: number): void

设置每次取出的事件包的数据条数，优先级高于setSize，和setSize同时调用时仅setRow生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型   | 必填 | 说明                                         |
| ------ | ------ | ---- | -------------------------------------------- |
| size   | number | 是   | 事件条数，单位为条。取值范围(0, 2^31-1]，超出范围会抛异常。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息            |
| -------- | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11104001 | Invalid size value. Possible caused by the size value is less than or equal to zero. |

**示例：**

```ts
// 创建订阅数据持有者实例，holder3持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder3: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 设置每次取出的事件包的数据条数为1000条
holder3.setRow(1000);
```

### takeNext

takeNext(): AppEventPackage

获取订阅事件。

系统根据setSize设置的数据大小阈值或setRow设置的条数来取出订阅事件数据，默认取1条订阅事件。当订阅事件数据全部被取出时返回null。

当setRow和setSize同时调用时仅setRow生效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型                                | 说明                                                   |
| ----------------------------------- | ------------------------------------------------------ |
| [AppEventPackage](#appeventpackage) | 取出的事件包对象，订阅事件数据被全部取出后会返回null。 |

**示例：**

```ts
// 创建订阅数据持有者实例，holder4持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder4: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 获取订阅事件
let eventPkg: hiAppEvent.AppEventPackage | null = holder4.takeNext();
```


## AppEventInfo

提供事件信息的参数选项。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称      | 类型                    | 只读 | 可选 | 说明                                                         |
| --------- | ----------------------- | ---- | ---- | ------------------------------------------------------------ |
| domain    | string                  | 否 | 否   | 事件领域。事件领域名称支持数字、字母、下划线字符，需要以字母开头且不能以下划线结尾，长度非空且不超过32个字符。 |
| name      | string                  | 否 | 否   | 事件名称。首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过48个字符。 |
| eventType | [EventType](#eventtype) | 否 | 否   | 事件类型。                                                   |
| params    | object                  | 否 | 否   | 事件参数对象，包含每个事件参数的参数名和参数值。**系统事件中params包含的字段已由各系统事件定义，具体字段含义在各类系统事件指南的介绍中，例如[崩溃事件介绍](../../dfx/hiappevent-watcher-crash-events.md)。** 针对应用事件，[Write](#hiappeventwrite-1)打点写入的参数由开发者定义，其规格如下：<br>- 参数名为string类型，首字符必须为字母字符或`$`字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。如testName、\$123_name等。<br>- 参数值支持string、number、boolean、数组类型。string类型参数长度需在8*1024个字符以内，超出后会和对应的参数名一同被丢弃；number类型参数取值需在Number.MIN_SAFE_INTEGER~Number.MAX_SAFE_INTEGER范围内，超出可能会产生不确定值；数组类型参数中的元素类型只能全为string、number、boolean中的一种，且元素个数需在100以内，超出部分即从第101个元素开始会被丢弃。<br>- 参数个数需在32个以内，超出的参数会做丢弃处理。 |


## AppEventPackage

提供订阅返回的事件包的参数定义。可用于获取事件包的详细信息，事件包由[takeNext](#takenext)接口获得。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称      | 类型     | 只读 | 可选 | 说明                           |
| --------- | -------- | ---- | ---- | ------------------------------ |
| packageId | number   | 否 | 否   | 事件包ID，从0开始自动递增。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。    |
| row       | number   | 否 | 否   | 事件包的事件数量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。             |
| size      | number   | 否 | 否   | 事件包的事件大小，单位为byte。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| data      | string[] | 否 | 否   | 事件包的事件信息。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。             |
| appEventInfos<sup>12+</sup> | Array<[AppEventInfo](#appeventinfo)> | 否 | 否   | 事件对象集合。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |


## AppEventGroup<sup>11+</sup>

提供订阅返回的事件组的参数定义。可用于获取事件组的详细信息，事件组常在[Watcher](#watcher)的onReceive回调中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称          | 类型                            | 只读 | 可选  | 说明          |
| ------------- | ------------------------------- | ---- | ---- | ------------- |
| name          | string                          | 否 | 否   | 事件名称。     |
| appEventInfos | Array<[AppEventInfo](#appeventinfo)> | 否 | 否   | 事件对象集合。 |


## hiAppEvent.write

write(info: AppEventInfo, callback: AsyncCallback&lt;void&gt;): void

应用事件打点方法，将AppEventInfo类型的事件进行存储，使用callback方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入系统事件（[Event](#hiappeventevent)中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher](#hiappeventaddwatcher)）进行订阅。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名   | 类型                           | 必填 | 说明           |
| -------- | ------------------------------ | ---- | -------------- |
| info     | [AppEventInfo](#appeventinfo) | 是   | 应用事件对象。其内部定义的事件名称建议避免与[Event](#hiappeventevent)中定义的系统事件名称常量产生冲突。 |
| callback | AsyncCallback&lt;void&gt;      | 是   | 打点回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11100001 | Function disabled. Possible caused by the param disable in ConfigOption is true. |
| 11101001 | Invalid event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101002 | Invalid event name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101003 | Invalid number of event parameters. Possible caused by the number of parameters is over 32. |
| 11101004 | Invalid string length of the event parameter. |
| 11101005 | Invalid event parameter name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101006 | Invalid array length of the event parameter. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 应用事件打点，使用callback方式作为异步回调
hiAppEvent.write({
  domain: "test_domain",
  name: "test_event",
  eventType: hiAppEvent.EventType.FAULT,
  params: eventParams,
}, (err: BusinessError) => {
  if (err) {
    hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
    return;
  }
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
});
```


## hiAppEvent.write

write(info: AppEventInfo): Promise&lt;void&gt;

应用事件打点方法，将AppEventInfo类型的事件进行存储，使用Promise方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入系统事件（[Event](#hiappeventevent)中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher](#hiappeventaddwatcher)）进行处理。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型                           | 必填 | 说明           |
| ------ | ------------------------------ | ---- | -------------- |
| info   | [AppEventInfo](#appeventinfo) | 是   | 应用事件对象。其中的事件名称建议避免与[Event](#hiappeventevent)中定义的系统事件名称常量冲突混淆。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                                      |
| -------- | --------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11100001 | Function disabled. Possible caused by the param disable in ConfigOption is true. |
| 11101001 | Invalid event domain. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101002 | Invalid event name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101003 | Invalid number of event parameters. Possible caused by the number of parameters is over 32. |
| 11101004 | Invalid string length of the event parameter. |
| 11101005 | Invalid event parameter name. Possible causes: 1. Contain invalid characters; 2. Length is invalid. |
| 11101006 | Invalid array length of the event parameter. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 应用事件打点，使用Promise方式作为异步回调
hiAppEvent.write({
  domain: "test_domain",
  name: "test_event",
  eventType: hiAppEvent.EventType.FAULT,
  params: eventParams,
}).then(() => {
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});
```


## hiAppEvent.addProcessor<sup>11+</sup>

addProcessor(processor: Processor): number

添加数据处理者配置信息，用于配置处理者接收的事件名等信息。事件发生后处理者可以接收事件。

该接口为同步接口，包含耗时操作。为了确保性能，建议使用[addProcessorFromConfig](#hiappeventaddprocessorfromconfig20)异步接口或者交由子线程执行。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型        | 必填 | 说明              |
| ---------  | ---------- | ---- | -------------    |
| processor  | [Processor](#processor11)  | 是   | 上报事件的数据处理者。|

**返回值：**

| 类型    | 说明                   |
| ------ | ---------------------- |
| number | 所添加上报事件数据处理者的ID，标识唯一数据处理者，可用于移除数据处理者。 添加失败返回-1，添加成功返回大于0的值。 |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    let processor: hiAppEvent.Processor = {
      name: 'analytics_demo'
    };
    let id: number = hiAppEvent.addProcessor(processor);
    hilog.info(0x0000, 'hiAppEvent', `addProcessor event was successful, id=${id}`);
} catch (error) {
    hilog.error(0x0000, 'hiAppEvent', `failed to addProcessor event, code=${error.code}`);
}
```


## hiAppEvent.addProcessorFromConfig<sup>20+</sup>

addProcessorFromConfig(processorName: string, configName?: string): Promise&lt;number&gt;

<!--RP1-->

添加数据处理者配置信息，通过配置文件配置处理者接收的事件名等信息，事件发生后处理者可以接收事件，使用Promise异步回调。
<!--RP1End-->

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型        | 必填 | 说明              |
| ---------  | ---------- | ---- | -------------    |
| processorName  |  string  | 是   | <!--RP2-->数据处理者的名称。名称只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。<!--RP2End-->|
| configName  |  string  | 否   | <!--RP3-->数据处理者的配置名称，支持从配置文件中加载对应配置，默认为“SDK_OCG”。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。<!--RP3End-->|

**返回值：**

| 类型    | 说明                   |
| ------ | ---------------------- |
| Promise&lt;number&gt; | Promise对象。返回添加的事件数据处理者的唯一ID，可用于移除该数据处理者。 添加失败返回11105001错误码。 |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 11105001     | Invalid parameter value. Possible causes: 1. Incorrect parameter length; 2. Incorrect parameter format. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addProcessorFromConfig("test_name").then((processorId) => {
  hilog.info(0x0000, 'hiAppEvent', `Succeeded in adding processor from config, processorId=${processorId}`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `Failed to add processor from config, code: ${err.code}, message: ${err.message}`);
});
```


## hiAppEvent.removeProcessor<sup>11+</sup>

removeProcessor(id: number): void

移除上报事件的数据处理者。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型    | 必填 | 说明                         |
| ------| ------- | ---- | --------------------------- |
| id    | number  | 是   | 上报事件数据处理者ID。值大于0。由调用[addProcessor](#hiappeventaddprocessor11)接口返回值所得。|

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    let processor: hiAppEvent.Processor = {
      name: 'analytics_demo'
    };
    let id: number = hiAppEvent.addProcessor(processor);
    // 根据添加数据处理者返回的标识id移除特定数据处理者
    hiAppEvent.removeProcessor(id);
} catch (error) {
    hilog.error(0x0000, 'hiAppEvent', `failed to removeProcessor event, code=${error.code}`);
}
```


## hiAppEvent.setUserId<sup>11+</sup>

setUserId(name: string, value: string): void

设置用户ID值。用于在配置[Processor](#processor11)数据处理者时进行关联。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型                      | 必填 | 说明           |
| --------- | ------------------------- | ---- | -------------  |
| name      | string                    | 是   | 用户ID的key。只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。   |
| value     | string                    | 是   | 用户ID的值。长度不超过256，当值为null或空字符串时，则清除用户ID。 |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  hiAppEvent.setUserId('key', 'value');
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to setUserId event, code=${error.code}`);
}
```


## hiAppEvent.getUserId<sup>11+</sup>

getUserId(name: string): string

获取通过setUserId接口设置的value值。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型                    | 必填 | 说明         |
| --------- | ----------------------- | ---- | ----------  |
| name      | string                  | 是   | 用户ID的key。只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。|

**返回值：**

| 类型    | 说明                            |
| ------ | ------------------------------- |
| string | 用户ID的值。没有查到返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.setUserId('key', 'value');
try {
  let value: string = hiAppEvent.getUserId('key');
  hilog.info(0x0000, 'hiAppEvent', `getUserId event was successful, userId=${value}`);
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to getUserId event, code=${error.code}`);
}
```


## hiAppEvent.setUserProperty<sup>11+</sup>

setUserProperty(name: string, value: string): void

设置用户属性值。用于在配置[Processor](#processor11)数据处理者时进行关联。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型                      | 必填 | 说明           |
| --------- | ------------------------- | ---- | -------------- |
| name      | string                    | 是   | 用户属性的key。只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。  |
| value     | string                    | 是   | 用户属性的值。长度不超过1024，当值为null或空字符串时，则清除用户属性。  |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  hiAppEvent.setUserProperty('key', 'value');
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to setUserProperty event, code=${error.code}`);
}
```


## hiAppEvent.getUserProperty<sup>11+</sup>

getUserProperty(name: string): string

获取通过setUserProperty接口设置的value值。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名     | 类型                    | 必填 | 说明          |
| --------- | ----------------------- | ---- | ----------    |
| name      | string                  | 是   | 用户属性的key。只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。|

**返回值：**

| 类型    | 说明                             |
| ------ | -------------------------------- |
| string | 用户属性的值。没有查到返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息          |
| ------- | ----------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.setUserProperty('key', 'value');
try {
  let value: string = hiAppEvent.getUserProperty('key');
  hilog.info(0x0000, 'hiAppEvent', `getUserProperty event was successful, userProperty=${value}`);
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to getUserProperty event, code=${error.code}`);
}
```


## hiAppEvent.clearData

clearData(): void

应用事件打点数据清理方法，将当前应用存储在本地的打点数据进行清除。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**示例：**

```ts
hiAppEvent.clearData();
```


## hiAppEvent.configure

configure(config: ConfigOption): void

应用事件打点配置方法，支持配置打点开关和目录存储配额大小。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型                          | 必填 | 说明                     |
| ------ | ----------------------------- | ---- | ------------------------ |
| config | [ConfigOption](#configoption) | 是   | 应用事件打点配置项对象。 |

**错误码：**

以下错误码的详细介绍请参见[应用事件打点错误码](errorcode-hiappevent.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 11103001 | Invalid max storage quota value. Possible caused by incorrectly formatted. |

**示例：**

```ts
// 配置打点开关为关闭状态
let config1: hiAppEvent.ConfigOption = {
  disable: true,
};
hiAppEvent.configure(config1);

// 配置文件目录存储配额为100M
let config2: hiAppEvent.ConfigOption = {
  maxStorage: '100M',
};
hiAppEvent.configure(config2);
```


## ConfigOption

提供对应用事件打点功能的配置选项。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称       | 类型    | 只读 | 可选 | 说明                                                         |
| ---------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| disable    | boolean | 否 | 是   | 打点功能开关，默认值为false。true：关闭打点功能，false：开启打点功能。 |
| maxStorage | string  | 否 | 是   | 打点数据存放目录的配额大小，默认值为“10M”。建议配额大小不超过10M，配额过大可能会影响接口效率。<br>在目录大小超出配额后，下次打点会触发对目录的清理操作：按从旧到新的顺序逐个删除打点数据文件，直到目录大小不超出配额时结束。<br>配额值字符串规格如下：<br>- 配额值字符串只由数字字符和大小单位字符（单位字符支持[b\|k\|kb\|m\|mb\|g\|gb\|t\|tb]，不区分大小写）构成。<br>- 配额值字符串必须以数字开头，后面可以选择不传单位字符（默认使用byte作为单位），或者以单位字符结尾。 |


## Processor<sup>11+</sup>

可以上报事件的数据处理者对象。用于事件的上报和管理，开发者可自定义数据处理配置，满足不同的数据处理需求。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称                | 类型                     | 只读 | 可选 | 说明                                                                                                        |
| ------------------- | ----------------------- | ---- | ---- | ---------------------------------------------------------------------------------------------------------- |
| name                | string                  | 否 | 否   | 数据处理者的名称。名称只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                                                                           |
| debugMode           | boolean                 | 否 | 是   | 是否开启debug模式，默认值为false。配置值为true表示开启debug模式，false表示不开启debug模式。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                    |
| routeInfo           | string                  | 否 | 是   | 服务器位置信息，默认为空字符串。传入字符串长度不能超过8KB，超过时会被置为默认值。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                                                                   |
| appId               | string                  | 否 | 是   | 应用id，默认为空字符串。传入字符串长度不能超过8KB，超过时会被置为默认值。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| onStartReport       | boolean                 | 否 | 是   | 数据处理者在启动时是否上报事件，默认值为false。配置值为true表示上报事件，false表示不上报事件。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                   |
| onBackgroundReport  | boolean                 | 否 | 是   | 当应用程序进入后台时是否上报事件，默认值为false。配置值为true表示上报事件，false表示不上报事件。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                 |
| periodReport        | number                  | 否 | 是   | 事件定时上报时间周期，单位为秒。传入数值必须大于或等于0，小于0时会被置为默认值0，不进行定时上报。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                                |
| batchReport         | number                  | 否 | 是   | 事件上报阈值，当事件条数达到阈值时上报事件。传入数值必须大于0且小于1000，不在数值范围内会被置为默认值0，不进行上报。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                         |
| userIds             | string[]                | 否 | 是   | 数据处理者可以上报的用户ID的name数组。name对应[setUserId](#hiappeventsetuserid11)接口的name参数。默认为空数组。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。    |
| userProperties      | string[]                | 否 | 是   | 数据处理者可以上报的用户属性的name数组。name对应[setUserProperty](#hiappeventsetuserproperty11)接口的name参数。默认为空数组。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。   |
| eventConfigs        | [AppEventReportConfig](#appeventreportconfig11)[]  | 否 | 是   | 数据处理者可以上报的事件描述配置数组。默认为空数组。<br>**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。                                                                                 |
| configId<sup>12+</sup> | number | 否 | 是 | 数据处理者配置id。传入数值必须大于或等于0，小于0时会被置为默认值0。传入的值大于0时，与数据处理者的名称name共同唯一标识数据处理者。<br>**原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| customConfigs<sup>12+</sup> | Record\<string, string> | 否 | 是 | 自定义扩展参数。传入参数名和参数值不符合规格会默认不配置扩展参数，其规格定义如下：<br>- 参数名为string类型，首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。<br>- 参数值为string类型，参数值长度需在1024个字符以内。<br>- 参数个数需在32个以内。<br>**原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| configName<sup>20+</sup>    | string                  | 否 | 是   | <!--RP4-->数据处理者的配置名称，支持从配置文件中加载对应配置，默认为空。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。<br>**原子化服务API：** 从API version 20开始，该参数支持在原子化服务中使用。<!--RP4End-->|


## AppEventReportConfig<sup>11+</sup>

数据处理者可以上报事件的描述配置。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称         | 类型    | 只读 | 可选 | 说明                                                          |
| ----------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| domain      | string  | 否 | 是   | 事件领域。默认为空字符串，事件领域名称支持数字、字母、下划线字符，需要以字母开头且不能以下划线结尾，长度非空且不超过32个字符。 |
| name        | string  | 否 | 是   | 事件名称。默认为空字符串，首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过48个字符。 |
| isRealTime  | boolean | 否 | 是   | 是否实时上报事件。默认值为false，配置值为true表示实时上报事件，false表示不实时上报事件。 |


## ParamType<sup>12+</sup>

type ParamType = number | string | boolean | Array&lt;string&gt;

事件自定义参数值的类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 类型                       | 说明                |
|--------------------------|-------------------|
| number                   | 表示值类型为数字。         |
| string                   | 表示值类型为字符串。        |
| boolean                  | 表示值类型为布尔值。        |
| Array&lt;string&gt;      | 表示值类型为字符串类型的数组。   |


## EventType

事件类型枚举。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称      | 值   | 说明           |
| --------- | ---- | -------------- |
| FAULT     | 1    | 故障类型事件。 |
| STATISTIC | 2    | 统计类型事件。 |
| SECURITY  | 3    | 安全类型事件。 |
| BEHAVIOR  | 4    | 行为类型事件。 |


## hiAppEvent.domain<sup>11+</sup>

提供领域名称常量。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称 | 类型   | 只读   | 说明       |
| ---  | ------ | ------ | ---------- |
| OS   | string | 是 | 系统领域。 |


## hiAppEvent.event

提供事件名称常量。包含系统事件名称常量和应用事件名称常量，其中应用事件名称常量是为开发者在调用[Write](#hiappeventwrite-1)接口进行应用事件打点时预留的可选自定义事件名称。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称                      | 类型   | 只读   | 说明                 |
| ------------------------- | ------ | ------ | -------------------- |
| USER_LOGIN                | string | 是 | 用户登录事件。预留的应用事件名称常量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。       |
| USER_LOGOUT               | string | 是 | 用户登出事件。预留的应用事件名称常量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。       |
| DISTRIBUTED_SERVICE_START | string | 是 | 分布式服务启动事件。预留的应用事件名称常量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| APP_CRASH<sup>11+</sup>   | string | 是 | 应用崩溃事件。系统事件名称常量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。       |
| APP_FREEZE<sup>11+</sup>  | string | 是 | 应用冻屏事件。系统事件名称常量。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。       |
| APP_LAUNCH<sup>12+</sup>  | string | 是 | 应用启动耗时事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。   |
| SCROLL_JANK<sup>12+</sup> | string | 是 | 应用滑动丢帧事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。   |
| CPU_USAGE_HIGH<sup>12+</sup> | string | 是 | 应用CPU高负载事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| BATTERY_USAGE<sup>12+</sup> | string | 是 | 应用24h功耗器件分解统计事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| RESOURCE_OVERLIMIT<sup>12+</sup> | string | 是 | 应用资源泄露事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| ADDRESS_SANITIZER<sup>12+</sup> | string | 是 | 应用地址越界事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| MAIN_THREAD_JANK<sup>12+</sup> | string | 是 | 应用主线程超时事件。系统事件名称常量。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| APP_KILLED<sup>20+</sup> | string | 是 | 应用查杀事件。系统事件名称常量。<br>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |


## hiAppEvent.param

提供参数名称常量。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

| 名称                            | 类型   | 只读   | 说明               |
| ------------------------------- | ------ | ------ | ------------------ |
| USER_ID                         | string | 是 | 用户自定义ID。     |
| DISTRIBUTED_SERVICE_NAME        | string | 是 | 分布式服务名称。   |
| DISTRIBUTED_SERVICE_INSTANCE_ID | string | 是 | 分布式服务实例ID。 |
