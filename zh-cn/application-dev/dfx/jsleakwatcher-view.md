# jsleakwatcher自定义可配置参数

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @lu_tao-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->


## configs参数格式

<!--code_no_check-->
```ts
以下configs参数为LeakWatcherConfig对象，对象中包含多个用于内存泄漏监测的可配置属性。

interface LeakWatcherConfig {
  objectWatcher: Array<string>;
  objectUniqueIDs: Array<number>;
  checkInterval: number;
  retainedVisibleThreshold: number;
  retainedInvisibleThreshold: number;
  maxStoredHeapDumps: number;
  dumpHeapWaitTimeMs: number;
  whiteList: Array<string>;
}
```


## configs参数说明

开发者可通过configs参数自定义配置泄漏监测选项。以下详细介绍参数类型、及作用。

| 参数| 含义| 说明
| ------- | ------- | ------- |
| objectWatcher: Array<string> | 被监测对象类型（如五大组件） | 若ID列表有配置，则该监测对象必定为自定义组件（CustomComponent） |
| objectUniqueIDs : Array<number> | 被监测对象ID列表（如自定义组件ID） | 高优先级执行，其它参数配置若与之冲突，优先该参数生效。例如：白名单中设置的对象类名id与自定义ID列表存在相同值时，生效ID列表参数。 |
| checkInterval : number | 每轮泄漏检测间隔时间 | 默认为30秒。 |
| retainedVisibleThreshold : number | 应用在前台泄漏个数达到设定值触发dump（如 5个） | GC/Dump阶段，阈值默认为5，大于等于5时触发Dump。 |
| retainedInvisibleThreshold : number | 应用在后台泄漏个数达到设定值触发dump（如 1个） | GC/Dump阶段，阈值默认为1，大于等于1时触发Dump。 |
| maxStoredHeapDumps : number | 最大dump保存个数（如 10个），避免磁盘空间占满 | 默认保存10个rawheap、10个jsleaklist文件，超过则删除时间戳最小的rawheap、jsleaklist文件。 |
| dumpHeapWaitTimeMs : number | 延迟执行dump，保证GC能调度且执行完再执行dump（如延迟5秒） | GC结束后默认延迟5秒执行dump，延迟间隔小于等于泄漏检测间隔时间；设置延迟时长超过泄漏间隔时长则默认与泄漏间隔时长保持一致。 |
| whiteList : Array<string> | 过滤不想监测的对象类名（ClassName） | 配置项冲突优先级：ID列表 > 白名单 > 被监测对象类型。 |
