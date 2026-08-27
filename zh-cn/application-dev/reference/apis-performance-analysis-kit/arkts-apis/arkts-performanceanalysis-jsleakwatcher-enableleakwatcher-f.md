# enableLeakWatcher

## 导入模块

```TypeScript
```

## enableLeakWatcher

```TypeScript
function enableLeakWatcher(isEnabled: boolean, configs: Array<string>, callback: Callback<Array<string>>): void
```

使能ArkTS对象泄漏检测。此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁。使用场景：  
- 对内存使用有严格要求的应用，需要持续监控内存泄漏情况。  
- 监控使用XComponent、NodeContainer、Window、CustomComponent、Ability等组件的应用是否发生泄漏。  
- 应用开发调试和测试阶段，快速发现内存泄漏问题。  
- 长时间运行的应用，需要定期检测内存泄漏。

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否使能ArkTS对象内存泄漏检测功能。true：开启ArkTS内存泄漏检测功能；false：关闭ArkTS内存泄漏检测功能。 |
| configs | Array & lt;string & gt; | 是 | 配置项，数组中每个元素为监测具体对象的类型。 可配置项包括：XComponent，NodeContainer，Window，CustomComponent和Ability。    **说明：**传入空数组代表监测以上全部对象。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，用于接收jsLeakWatcher.enableLeakWatcher接口返回的内存泄漏文件列表和虚拟机内存快照文件。 回调函数中传入一个数组对象，索引0为泄漏列表文件名，后缀为.jsleaklist；索引1为虚拟机内存快照文件名，后缀为.rawheap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001-参数isenabled无效) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002-参数config无效) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003-参数callback无效) | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
let config: Array<string> = ['XComponent'];
// 监测ArkTS对象XComponent的内存泄漏
// 传入空数组代表监测全部对象
jsLeakWatcher.enableLeakWatcher(true, config, (filePath: Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## enableLeakWatcher

```TypeScript
function enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback<Array<string>>): void
```

使能ArkTS对象泄漏检测。此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁；通过configs可配置项参数，自定义设置监测项各属性，相比较之前极大提升了泄漏检测性能。

> **注意：**
> 
> 当前jsLeakWatcher泄漏检测性能开销较大，会导致应用卡顿，建议增大检测间隔时间，减少卡顿频率。
> 使用场景：
- 对性能要求较高的应用，需要通过配置检测间隔、阈值等参数来平衡检测精度和性能开销。  
- 大型应用或复杂应用，需要精细控制泄漏检测的参数，如检测间隔、泄漏阈值、最大dump数量等。  
- 使用特定组件（如CustomComponent、Window、Ability等）的应用，需要针对性监控这些组件的泄漏。  
- 对内存管理有严格要求的应用，需要设置过滤规则排除某些不需要监控的对象。  
- 长时间运行或需要持续监控的应用，需要合理设置检测间隔和最大保存数量。

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 是否使能ArkTS对象内存泄漏检测功能。 true：开启ArkTS内存泄漏检测功能。 false：关闭ArkTS内存泄漏检测功能。 |
| configs | [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | 是 | LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。    **说明：**对象中参数类型传入空值或假值代表该属性设置为默认值。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，用于接收泄漏检测的导出文件路径。回调函数中传入一个数组对象，索引0为泄漏列表文件名，后缀为.jsleaklist；索引1为虚拟机 内存快照文件名，后缀为.rawheap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001-参数isenabled无效) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002-参数config无效) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003-参数callback无效) | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
// 监测ArkTS对象CustomComponent和Window的内存泄漏
// 对象中类型传入空值或假值代表该属性设置为默认值
let config: jsLeakWatcher.LeakWatcherConfig = {
    monitorObjectTypes: jsLeakWatcher.MonitorObjectType.CUSTOM_COMPONENT | jsLeakWatcher.MonitorObjectType.WINDOW,
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
