# enableLeakWatcher

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## enableLeakWatcher

```TypeScript
function enableLeakWatcher(isEnabled: boolean, configs: Array<string>, callback: Callback<Array<string>>): void
```

ʹ��ArkTS����й©��⡣

�˽ӿ�ͨ��һ�ε��ü��ɼ��ArkTS������ڴ�й©����֮ǰ��Ҫ�����ĸ�������enable��watch��check��dump���ķ������Ӽ�ࡣ

**起始版本：** 20

<!--Device-jsLeakWatcher-function enableLeakWatcher(isEnabled: boolean, configs: Array<string>, callback: Callback<Array<string>>): void--><!--Device-jsLeakWatcher-function enableLeakWatcher(isEnabled: boolean, configs: Array<string>, callback: Callback<Array<string>>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | �Ƿ�ʹ��ArkTS�����ڴ�й©��⹦�ܡ�true������ArkTS�ڴ�й©��⹦�ܣ�false���ر�ArkTS�ڴ�й©��⹦�ܡ� |
| configs | Array&lt;string&gt; | 是 | �����������ÿ��Ԫ��Ϊ�������������͡�<br>�������������XComponent��NodeContainer��Window��CustomComponent��Ability��<br>**˵��**���������������������ȫ������ |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | �ص����������ڽ���jsLeakWatcher.enableLeakWatcher�ӿڷ��ص��ڴ�й©�ļ��б���������ڴ�����ļ���<br>�ص������д���һ��������������0Ϊй©�б��ļ�������׺Ϊ.jsleaklist������1Ϊ������ڴ�����ļ�������׺Ϊ.rawheap�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001--参数isenabled无效) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002--参数config无效) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003--参数callback无效) | The parameter callback is invalid.Input parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

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

ʹ��ArkTS����й©��⡣

�˽ӿ�ͨ��һ�ε��ü��ɼ��ArkTS������ڴ�й©����֮ǰ��Ҫ�����ĸ�������enable��watch��check��dump���ķ������Ӽ�ࣻͨ��configs��������������Զ������ü��������ԣ���Ƚ�֮ǰ����������й©������ܡ�
> **ע��**  
>  
> ��ǰjsLeakWatcherй©������ܿ����ϴ󣬻ᵼ��Ӧ�ÿ��٣�������������ʱ�䣬���ٿ���Ƶ�ʡ�

**起始版本：** 24

<!--Device-jsLeakWatcher-function enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback<Array<string>>): void--><!--Device-jsLeakWatcher-function enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback<Array<string>>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | �Ƿ�ʹ��ArkTS�����ڴ�й©��⹦�ܡ�<br>true������ArkTS�ڴ�й©��⹦�ܡ�<br>false���ر�ArkTS�ڴ�й©��⹦�ܡ� |
| configs | [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | 是 | LeakWatcherConfig�������ͣ������а�����������ڴ�й©���Ŀ��������ԡ�<br>**˵��**�������в������ʹ����ֵ���ֵ��������������ΪĬ��ֵ�� |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | �ص����������ڽ���й©���ĵ����ļ�·����<br>�ص������д���һ��������������0Ϊй©�б��ļ�������׺Ϊ.jsleaklist������1Ϊ������ڴ�����ļ�������׺Ϊ.rawheap�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001--参数isenabled无效) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002--参数config无效) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003--参数callback无效) | The parameter callback is invalid.Input parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

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

