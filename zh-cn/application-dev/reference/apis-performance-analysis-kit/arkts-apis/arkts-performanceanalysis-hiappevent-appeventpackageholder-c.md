# AppEventPackageHolder

订阅数据持有者类，用于对事件信息进行处理。

**起始版本：** 9

<!--Device-hiAppEvent-class AppEventPackageHolder--><!--Device-hiAppEvent-class AppEventPackageHolder-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## constructor

```TypeScript
constructor(watcherName: string)
```

类构造函数，用于创建订阅数据持有者实例。先通过[addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md#addwatcher)添加事件观察者，再通过观察者名称关联到应用内已添加的观察者对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackageHolder-constructor(watcherName: string)--><!--Device-AppEventPackageHolder-constructor(watcherName: string)-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watcherName | string | 是 | 已通过[addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md#addwatcher)添加的事件观察者名称。若未通过addWatcher添加，则默认无数据。 |

**示例：**

```TypeScript
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

## setRow

```TypeScript
setRow(size: number): void
```

设置每次取出的事件包的数据条数，优先级高于setSize，和setSize同时调用时仅setRow生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackageHolder-setRow(size: int): void--><!--Device-AppEventPackageHolder-setRow(size: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 事件条数，单位为条。取值范围(0, 2^31-1]，超出范围会抛异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [11104001](../errorcode-hiappevent.md#11104001-非法的事件包大小值) | Invalid size value. Possibly caused by the size value is less than or equal to zero. |

**示例：**

```TypeScript
// 创建订阅数据持有者实例，holder3持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder3: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 设置每次取出的事件包的数据条数为1000条
holder3.setRow(1000);

```

## setSize

```TypeScript
setSize(size: number): void
```

设置每次取出的事件包的数据大小阈值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackageHolder-setSize(size: int): void--><!--Device-AppEventPackageHolder-setSize(size: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 数据大小阈值，单位为byte。取值范围[0, 2^31-1]，超出范围会抛异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [11104001](../errorcode-hiappevent.md#11104001-非法的事件包大小值) | Invalid size value. Possibly caused by the size value is less than or equal to zero. |

**示例：**

```TypeScript
// 创建订阅数据持有者实例，holder2持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder2: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 设置每次取出事件包的数据大小阈值为1000byte
holder2.setSize(1000);

```

## takeNext

```TypeScript
takeNext(): AppEventPackage
```

获取订阅事件。

系统根据setSize设置的数据大小阈值或setRow设置的条数来取出订阅事件数据，默认取1条订阅事件。当订阅事件数据全部被取出时返回null。

当setRow和setSize同时调用时仅setRow生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackageHolder-takeNext(): AppEventPackage--><!--Device-AppEventPackageHolder-takeNext(): AppEventPackage-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppEventPackage](arkts-performanceanalysis-hiappevent-appeventpackage-i.md) | 取出的事件包对象，订阅事件数据被全部取出后会返回null。 |

**示例：**

```TypeScript
// 创建订阅数据持有者实例，holder4持有的数据为已通过addWatcher添加的观察者“Watcher1”监听到的事件
let holder4: hiAppEvent.AppEventPackageHolder = new hiAppEvent.AppEventPackageHolder("Watcher1");
// 获取订阅事件
let eventPkg: hiAppEvent.AppEventPackage | null = holder4.takeNext();

```

