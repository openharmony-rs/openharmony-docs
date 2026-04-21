# @ohos.hiviewdfx.jsLeakWatcher (ArkTS泄漏检测)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Lutao98-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

本模块提供了监控ArkTS对象是否发生泄漏的能力。

> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```


## jsLeakWatcher.enable

enable(isEnable: boolean): void

使能ArkTS对象泄漏检测，默认关闭。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| isEnable | boolean | 是 | 是否使能jsLeakWatcher。true：使能jsLeakWatcher；false：不使能jsLeakWatcher。 |

**示例：**

```js
jsLeakWatcher.enable(true);
```


## jsLeakWatcher.watch

watch(obj: object, msg: string): void

注册待检测泄漏的对象。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| obj | object | 是 | 需要检测的对象名。<br>**说明**：可传入任何类型对象。|
| msg | string | 是 | 自定义对象信息。 |

**示例：**

```js
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");
```


## jsLeakWatcher.check

check(): string

获取已通过jsLeakWatcher.watch注册发生泄漏的对象列表，触发GC后未被回收的对象会被标记为泄漏。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

**返回值：**

| 类型    | 说明                                                       |
| ------- | ---------------------------------------------------------- |
| string | 触发GC后未被回收的泄漏对象列表。<br>**说明**：check成功，返回JSON格式的泄漏对象列表；check失败，返回空字符串。 |

**示例：**
```js
let leakObjlist:string = jsLeakWatcher.check();
```


## jsLeakWatcher.dump

dump(filePath: string): Array&lt;string&gt;

导出泄漏列表和虚拟机内存快照。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| filePath | string | 是 | 导出信息生成的文件存放的路径。<br>**说明**：从API version 24开始，进程生命周期内，仅保留最新的一份快照信息。 |

**返回值：**

| 类型    | 说明                                                       |
| ------- | ---------------------------------------------------------- |
| Array&lt;string&gt; | 导出结果。分别为文件名后缀为.jsleaklist的泄漏列表和文件名后缀为.heapsnapshot虚拟机内存快照文件。<br>**说明**：dump成功，返回泄漏列表文件路径和虚拟机内存快照路径；dump失败，返回空数组。 |

**示例：**
<!--code_no_check-->
```js
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```


## jsLeakWatcher.enableLeakWatcher<sup>20+</sup>

enableLeakWatcher(isEnabled: boolean, configs: Array&lt;string&gt;, callback: Callback&lt;Array&lt;string&gt;&gt;): void

使能ArkTS对象泄漏检测。

此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁。


**系统能力**：SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | 是| 是否使能ArkTS对象内存泄漏检测功能。true：开启ArkTS内存泄漏检测功能；false：关闭ArkTS内存泄漏检测功能。|
| configs | Array&lt;string&gt; | 是| 配置项，数组中每个元素为监测具体对象的类型。<br>可配置项包括：XComponent，NodeContainer，Window，CustomComponent和Ability。<br>**说明**：传入空数组代表监测以上全部对象。 |
| callback | Callback&lt;Array&lt;string&gt;&gt; | 是| 回调函数，用于接收jsLeakWatcher.enableLeakWatcher接口的返回的内存泄漏的对象。<br>回调函数中传入一个数组对象，索引0为泄漏列表文件名，后缀为.jsleaklist；索引1为虚拟机内存快照文件名，后缀为.rawheap。|


**错误码：**

以下错误码的详细介绍请参见[JsLeakWatcher错误码](./errorcode-jsleakwatcher.md)。

| 错误码ID| 错误信息|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

<!--code_no_check-->
```ts
let config: Array<string> = ['XComponent'];
// 监测ArkTS对象XComponent的内存泄漏
// 传入空数组代表监测全部对象
jsLeakWatcher.enableLeakWatcher(true, config, (filePath: Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## jsLeakWatcher.enableLeakWatcher<sup>24+</sup>

enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback&lt;Array&lt;string&gt;&gt;): void

使能ArkTS对象泄漏检测。

此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁；通过configs可配置项参数，自定义设置监测项各属性，相比较之前极大提升了泄漏检测性能。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | 是| 是否使能ArkTS对象内存泄漏检测功能。<br>true：开启ArkTS内存泄漏检测功能。<br>false：关闭ArkTS内存泄漏检测功能。|
| configs | [LeakWatcherConfig](#leakwatcherconfig24) | 是| LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。<br>**说明**：对象中参数类型传入空值或假值代表该属性设置为默认值。|
| callback | Callback&lt;Array&lt;string&gt;&gt; | 是| 回调函数，用于接收jsLeakWatcher.enableLeakWatcher接口的返回的内存泄漏的对象。<br>回调函数中传入一个数组对象，索引0为泄漏列表文件名，后缀为.jsleaklist；索引1为虚拟机内存快照文件名，后缀为.rawheap。|


**错误码：**

以下错误码的详细介绍请参见[JsLeakWatcher错误码](./errorcode-jsleakwatcher.md)。

| 错误码ID| 错误信息|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

<!--code_no_check-->
```ts
enum MonitorObjectType {
  ALL = -1, 
  CUSTOM_COMPONENT = 1 << 0,
  WINDOW = 1 << 1,
  NODE_CONTAINER = 1 << 2,
  X_COMPONENT = 1 << 3,
  ABILITY = 1 << 4
};

interface LeakWatcherConfig {
  monitorObjectTypes: MonitorObjectType;
  objectUniqueIDs: Array<number>;
  checkInterval: number;
  fgLeakCountThreshold: number;
  bgLeakCountThreshold: number;
  maxStoredHeapDumps: number;
  dumpHeapWaitTimeMs: number;
  exclusionList: Array<string>;
};

// 监测ArkTS对象CustomComponent和Window的内存泄漏
// 对象中类型传入空值或假值代表该属性设置为默认值
let config: LeakWatcherConfig = {
    monitorObjectTypes: MonitorObjectType.CUSTOM_COMPONENT | MonitorObjectType.WINDOW,
    objectUniqueIDs: [],
    checkInterval: 10000,
    fgLeakCountThreshold: 5,
    bgLeakCountThreshold: 3,
    maxStoredHeapDumps: 5,
    dumpHeapWaitTimeMs: 5000,
    exclusionList: []
};
jsLeakWatcher.enableLeakWatcher(true, config, (filePath : Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## LeakWatcherConfig<sup>24+</sup>

LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

| 名称 | 类型 | 只读 | 可选 | 说明 | 
| ------- | ------- | ------- | ------- | ------- | 
| monitorObjectTypes | [MonitorObjectType](#monitorobjecttype24) | 否 | 否 | 被监测对象类型。<br>默认监测所有组件类型。 |
| objectUniqueIDs | Array&lt;number&gt; | 否   | 是   | 被监测泄漏对象ID列表。<br>只作用于自定义组件，不会影响其他组件类型的监测。<br>例如：白名单中设置的对象类名ID与自定义ID列表存在相同值时，生效自定义ID列表参数。<br>默认为空数组。 |
| checkInterval | number | 否 | 是 | 每轮泄漏检测间隔时间，单位：ms。<br>默认为30秒。 |
| fgLeakCountThreshold | number | 否 | 是 | 应用在前台泄漏个数达到设定值触发dump。<br>GC/Dump阶段，大于等于5时触发Dump。<br>阈值默认为5。 |
| bgLeakCountThreshold | number | 否 | 是 | 应用在后台泄漏个数达到设定值触发dump。<br>GC/Dump阶段，大于等于1时触发Dump。<br>阈值默认为1。 |
| maxStoredHeapDumps | number | 否 | 是 | 最大dump保存个数，避免磁盘空间占满，超过则删除时间戳最小的rawheap、jsleaklist文件。<br>默认保存10个rawheap、10个jsleaklist文件。 |
| dumpHeapWaitTimeMs | number | 否 | 是 | 延迟执行dump，保证GC能调度且执行完再执行dump，延迟间隔小于等于泄漏检测间隔时间，单位：ms。<br>设置延迟时长超过泄漏间隔时长则默认与泄漏间隔时长保持一致。<br>若无新增泄漏对象将不会触发dump。<br>GC结束后默认延迟5秒执行dump。 |
| exclusionList | Array&lt;string&gt; | 否 | 是 | 过滤不想监测的对象类名。<br>作用于Window、CustomComponent和Ability组件，不会影响其他组件类型的过滤。<br>存在混淆问题时无法进行过滤，只在开发态生效。<br>配置项冲突优先级：ID列表 > 白名单。<br>默认为空数组。 |


## MonitorObjectType<sup>24+</sup>

需要监控的组件对象类型枚举。

**系统能力**：SystemCapability.HiviewDFX.HiChecker

| 名称 | 值 | 说明 |
| ------- | ------- | ------- |
| ALL | -1 | 监测所有组件类型。 |
| CUSTOM_COMPONENT | 1 << 0 | 监测自定义组件类型。 |
| WINDOW | 1 << 1 | 监测Window组件类型。 |
| NODE_CONTAINER | 1 << 2 | 监测NodeContainer组件类型。 |
| X_COMPONENT | 1 << 3 | 监测XComponent组件类型。 |
| ABILITY | 1 << 4 | 监测Ability组件类型。 |