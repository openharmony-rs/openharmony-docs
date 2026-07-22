# addWatcher

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addWatcher

```TypeScript
function addWatcher(watcher: Watcher): AppEventPackageHolder
```

添加事件观察者。可通过事件观察者的回调函数监听事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function addWatcher(watcher: Watcher): AppEventPackageHolder--><!--Device-hiAppEvent-function addWatcher(watcher: Watcher): AppEventPackageHolder-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watcher | [Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-watcher-i.md) | 是 | 事件观察者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | 订阅数据持有者。订阅失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11102001](../errorcode-hiappevent.md#11102001-非法的观察者名称) | Invalid watcher name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102002](../errorcode-hiappevent.md#11102002-非法的过滤事件领域) | Invalid filtering event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102003](../errorcode-hiappevent.md#11102003-非法的条数值) | Invalid row value. Possibly caused by the row value is less than zero. |
| [11102004](../errorcode-hiappevent.md#11102004-非法的大小值) | Invalid size value. Possibly caused by the size value is less than zero. |
| [11102005](../errorcode-hiappevent.md#11102005-非法的超时值) | Invalid timeout value. Possibly caused by the timeout value is less than zero. |

**示例：**

方法一：设置回调条件triggerCondition，实现onTrigger()回调。当满足回调条件时，系统将自动触发回调。

```TypeScript
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

在手动处理订阅事件的方法中，由于事件可能未生成或日志信息未抓取完成，建议在进程启动后延时重试调用takeNext()获取此类事件。

```TypeScript
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

```TypeScript
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
        hilog.info(0x0000, 'hiAppEvent', `event=${JSON.stringify(eventInfo)}`);
      }
    }
  }
});

```

